# Yode

Yode is a fork of Node.js that replaces its event loop with GUI message loop,
it is usually used together with the [Yue library](http://libyue.com).

## Changes to Node.js

* The message loop is replaced with native GUI message loops:
  * On Linux it is GTK+ event loop;
  * On macOS it is Cocoa run loop;
  * On Windows it is win32 message loop.
* The process will not automatically quit when there is no work, you have to
  call the native APIs to quit the GUI message loop.
* The process will quit when **BOTH** the GUI message loop and Node event loop
  have quit. So if there are still Node.js requests pending, the process will
  wait until all of them have finished.
* There is a new `process.versions.yode` property added.
* The `process.stdin` is not supposed to work.
* On Windows the executable is a GUI program instead of a Console program, so
  there is no console attached and REPL won't work.

## Usage

The prebuilt binaries can be found in the Releases page, modules installed by
npm can be used directly in Yode.

Note that it is strong recommended to install official Node.js that has the same
version with Yode, otherwise native modules installed by npm may not work
correctly in Yode.

## Build

```bash
$ node ./build.js [x64|ia32]
```

## Contributions

By sending a pull request, you are agreeing to transfer the copyright of your
code to Cheng Zhao.

## License

The MIT license.
