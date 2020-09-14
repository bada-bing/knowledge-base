The chapter devoted to JS
[storybook.js](https://storybook.js.org/docs/basics/introduction/)

# Module Formats
ES5 and prior versions were using IIFE and Revealing Module Pattern to implement the **module** pattern

A module format is a syntax used to define modules
Some of the most widely adopted formats:
1. [CommonJS](http://www.commonjs.org/) - Used in Node.js
   - `require()` and `module.exports()`
   - `var dep1 = require('./dep1.js')`
3. [Asynchronous Module Definition (AMD)](https://github.com/amdjs/amdjs-api/wiki/AMD) - Used in Browsers
   - `define([dependency_array], function (dep1, dep2){...})`
4. [Universal Module Definition (UMD)](https://github.com/umdjs/umd) - Used in both Browsers and Node.js
   - uses AMD as a base, with special-casing added to handle CommonJS compatibility
5. System.register
   - designed to support ES6 module syntax support in ES5
6. ES6 Module Format - native module format
   - `import` and `export` tokens to import/export a module's public API

# Module Loaders
A module loader interprets and loads a module written in a certain module format

- runs at a runtime:
1. you load the module loader in the browser
2. you tell the module loader what is the main app file to load
3. the module loader downloads and interprets the main app file
4. the module loader downloads files as needed

RequireJS - loader for modules in AMD format
SystemJS - loader for AMD, CommonJS, UMD & system.register

# Module Bundler
Replaces Module Loaders
- In contrast to Module Loaders it run at **build time**!
1. You run the module bundler to generate a bundle file at build time (e.g., bundle.js)
2. you load the bundle in the browser

Webpack - bundler for AMD, CommonJS, ES6 modules
