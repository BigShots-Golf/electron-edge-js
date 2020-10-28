# .NET and Node.js in-process on Electron

This is a fork of [edge-js](https://github.com/agracio/edge-js) adapted to support [Electron](https://github.com/electron/electron/).

Compatible with

    - Electron 10.x - Node.js v12.16.3
    - Electron 10.x - Node.js v12.16.3

Usage is the same as edge or edge-js, replace `require('edge')` or `require('edge-js')` with `require('electron-edge-js')`:

    ```bash
    npm install electron-edge-js
    ```

    ```diff
    -var edge = require('edge-js');
    +var edge = require('electron-edge-js');

    var helloWorld = edge.func(function () {/*
        async (input) => {
            return ".NET Welcomes " + input.ToString();
        }
    */});
    ```

## Requirements (Windows)

You must install [Microsoft Visual C++ Redistributable (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

## Why use `electron-edge-js`

Electron is built using specific version of Node.js. In order to use `edge` in Electron project you would need to recompile it using the same Node.js version and Electron headers.

`electron-edge-js` comes precompiled with correct Node.js versions and headers.

## Differences from `electron-edge`

* Uses same codebase as `edge-js` that comes with both latest code changes from `edge` project and additional fixes and improvements available in `edge-js` project.
* Supports majority of Electron versions.

## Quick start

Simple app that shows how to work with .NET Core using compiled C# libraries. [electron-edge-js-quick-start](https://github.com/agracio/electron-edge-js-quick-start)

## Documentation

For full documentation please see see original [edge-js](https://github.com/agracio/edge-js) repo.

## Building

To build the app for the latest Node version, 15.0.1 as of 2020-10-28, with the latest Electron version of 10.1.5,
using Visual Studio 2019 enter the following in the base directory of the application:

```bash
node-gyp configure build --target=v10.1.5 --dist-url=https://electronjs.org/headers -v15.0.1
```