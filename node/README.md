1. [Programming Paradigms](###Paradigms)
    1. [Node Version Management](###NVM)
    1. [Mono-Repos](###Mono-Repos)
    1. [Event-Driven-Nature of Node](###Event-Driven-Nature)
    1. [Child-Processes in Node](###Child-Processes)
    1. [Streams](###Streams)
1. [Other](###Other)
    1. [Known Issues](###Issues)
    1. [Frequently used commands](###Frequently_used_commands)
1. [Configuration and Other Files](###Files)
1. [Interesting and Useful Facts](###FunFacts)
1. [Useful NPM Modules](##Modules)

## Paradigms ##
### NVM ###
This is the initial page about Node
[nvm](https://github.com/nvm-sh/nvm) & [nvm-windows](https://github.com/coreybutler/nvm-windows) for managing multiple versions of Node.js
* similar to virtual-env in Python - [article](https://www.sitepoint.com/quick-tip-multiple-versions-node-nvm/)
* [install on Ubuntu 14 ](https://www.liquidweb.com/kb/how-to-install-node-js-via-nvm-node-version-manager-on-ubuntu-14-04-lts/)
* [n - alternative to nvm](https://github.com/tj/n)

### Mono-Repos
- [storybook, lerna typescript combined](https://dev.to/shnydercom/monorepos-lerna-typescript-cra-and-storybook-combined-4hli)

### Event-Driven-Nature ###
*[ARTICLE](https://jscomplete.com/learn/node-beyond-basics/node-events)*

HTTP requests, responses and streams (HTTP req and res are streams as well) implement EventEmitter Module (to emit and listen for events)
- specified callback functions act as event handlers (e.g., fs.readFile)
    * callback - function you pass to other functions
- Promises: alternative to callbacks:
    - a promise object allows us to handle success and error cases separately and it allows us to chain multiple asynchronous calls instead of nesting them
- Third Approach: Async Functions
- EventEmitter Module
    - The EventEmitter is a module that facilitates communication between objects in Node.js This module is at the core of Node's async event-driven architecture!
    - Emitter object emits named event that cause previously registered listeners to be called
    - So, an emitter object basically has two main features:
        - Emitting named events
        - Registering and unregistering listener functions

### Child-Processes ###
* [executing-shell-commands-with-node-js/](https://stackabuse.com/executing-shell-commands-with-node-js/)

### Streams ###
* [concat-stream](https://www.npmjs.com/package/concat-stream) - return a combined final result/output from the readable stream
* [Node Streams - Everything you need to know](https://www.freecodecamp.org/news/node-js-streams-everything-you-need-to-know-c9141306be93/)
* [Node.js Streams Cheat Sheet](https://devhints.io/nodejs-stream)


## Other ##

1. [SO - **Remove** Node.js from windows](https://stackoverflow.com/questions/20711240/how-to-completely-remove-node-js-from-windows)
1. [npx](https://www.npmjs.com/package/npx) - runs the specified command from a certain package/binary
    - and if the package is not installed it will first install it
1. [Node script running forever](https://github.com/foreversd/forever)
1. [NPM Semantic Versioning](https://docs.npmjs.com/about-semantic-versioning)
    - [semver.org](https://semver.org/)
    - [NPM Semver Calculator](https://semver.npmjs.com/)
    - [SO - Diff between tilde and caret in npm semver](https://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json)

### Issues ###
1. If you have the issue with node-sass
	- install node-sass version 4.12.0, and after that worked for me. npm install node-sass@4.12.0 --save
		- [Source of the answer SO](https://stackoverflow.com/questions/46515077/unable-to-install-node-sass-in-my-project/51530331#51530331)

1. npm fix: "Missing write access" [npm WSL](https://flaviocopes.com/npm-fix-missing-write-access-error/)
	- sudo chown -R $USER /usr/local/lib/node_modules
		- this command, I only had to remove /local from the directory path
	- that should solve problem of installing in WSL
sometime it helps to use "sudo"

### Frequently_used_commands ###
npm list -g --depth=0
	- check the globally installed package version

npm link
	- https://medium.com/dailyjs/how-to-use-npm-link-7375b6219557


## Files ##

### Configuration Files
- stored in the root directory of the project
- webpack.config.js
[*NOTE*] If a webpack.config.js is present, the webpack command picks it up by default
    - otherwise, you can specify the config file (in cmd) with --config (useful for more complex configurations that need to be split into multiple files)
- vue.config.js (used as a wrapper around webpack.config.js)

### .npmrc ###
- set in the root of a project
- important properties
    - [registry](https://docs.npmjs.com/misc/registry) - the (npm) JS package registry
        - to resolve packages by name and version, npm talks to a registry website that implements the CommonJS Package Registry specification for reading package info.
    - in general, many fileextensions end with "rc" (e.g., .eslintrc)
        - rc stands for "runcom" -> "run commands"
    - [configuring-your-npmrc-for-an-optimal-nodejs-envir](https://dzone.com/articles/configuring-your-npmrc-for-an-optimal-nodejs-envir-2)
    - [configuring-your-registry-settings-as-an-npm-enterprise-user](https://docs.npmjs.com/configuring-your-registry-settings-as-an-npm-enterprise-user)


### FunFacts ###
* Change color of Node.js console output
* Package-lock.json locks specific versions of projects
* WebAssembly in Node.js

## Modules ##
* https://github.com/nock/nock
	- Mock HTTP server (for mocking responses)
* Puppeeter and Chrome in Node.js
* Web Scraper - node-osmosis
* Backpack - minimalistic build system for Node.js
* [strong-pm.io/](http://strong-pm.io/) - Process Manager for Node.js

### Express - Web Server ###
- Alternatives: Koa uses async/await “out of the box.” Express is callback-oriented.
