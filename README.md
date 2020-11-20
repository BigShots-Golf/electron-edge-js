# .NET and Node.js in-process on Electron

This is a fork of [edge-js](https://github.com/agracio/edge-js) adapted to support [Electron](https://github.com/electron/electron/).

Compatible with

    - Electron 10.x - Node.js v12.16.3
    - Electron 10.x - Node.js v15.0.1

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

## Add new Node Version

1. Update the Readme.md file with the latest version being used. Doing a find/replace of the current version is the easist way to ensure all documentation is updated.
1. Open up the `lib/edge.js` file and go to the `versionMap` array which should start around line 15. Add the latest Node version to the array.
1. Open up the `tools/buildall.bat` file and add the latest node version to the end of the prior release listed on line 2. For example, if you added 15.0.2 it would look like this: `"%~dp0\build.bat" release 12.16.3 15.0.1 15.0.2`

## Building

To build the app for the latest Node version, 15.0.1 as of 2020-10-28, with the latest Electron version of 10.1.5,
using Visual Studio 2019 or VS Code, enter the following in the base directory of the application:

```bash
node-gyp configure build --target=v10.1.5 --dist-url=https://electronjs.org/headers -v15.0.1
```

### Changing Electron Version

When you build the application, set the `--target` argument in the command to be the Electron version you want to build for. For example, to build for Electron 11.0.0 you would change the build command to be as follows:

```bash
node-gyp configure build --target=v11.0.0 --dist-url=https://electronjs.org/headers -v15.0.1
```

## Publish as Github Package

1. Open up a terminal to the root directory of this project
1. Run the build command above from the **Building** section. If the build succeeds, move on to the next step.
1. Enter the following command to publish the package:

```bash
yarn publish
```

If you do not have yarn installed, use npm

```bash
npm publish
```

1. Follow the prompts to publish the package
1. Commit the package.json file if you updated the package version
