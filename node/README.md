- [Paradigms](#paradigms)
- [Javascript](#javascript)
- [How Node Works?](#how-node-works)
  - [NVM](#nvm)
  - [Mono-Repos](#mono-repos)
  - [Event-Driven-Nature](#event-driven-nature)
  - [Child-Processes](#child-processes)
    - [Worker Thread](#worker-thread)
  - [Streams](#streams)
  - [Functional-Programming](#functional-programming)
- [Other](#other)
  - [Issues](#issues)
- [Files](#files)
  - [Configuration Files](#configuration-files)
  - [.npmrc](#npmrc)
- [FunFacts](#funfacts)
- [Tutorials](#tutorials)

This is the initial page about Node

## Paradigms ##

## Javascript
❗ This section is a Temporary solution - will be moved to separate Chapter

**Execution Context**
At each point of execution, the JavaScript engine must be able to tell which function it is currently executing. It must know the current context of execution. (Execution Context is created each time some function is executed)
* This is the internal JS concept which is used by JS engine to track the execution of the code
* Which code is currently executed? This question is answered by *Execution Context*
* The Execution Context is created per *Function Invocation* (each time any function is called, not once for each function)
- 2 Types of Context: The Execution Context and The Global Context (usually denoted as main; first thing to be created)
- Call stack: The order which determines the organization of Execution Contexts (helps to determine the order of execution)
  - it is based on LIFO approach (execution contexts are stacked one on top of other)
  - insertion: put execution context in call stack
  - popping: remove exectution context from call stack
- Stack Overflow: When you exceeded maximum amount of execution contexts in the stack

**Dynamic Binding**
The Process of determining the method to invoke at runtime (rather than at compile time)
- JS uses "this" and the prototype chain to achieve this
- Meaning of *this* (inside a method) is determined at runtime and the rules change depending on how the method is defined (arrow functions vs regular functions)
  - Arrow Functions do not have their own scope - they bind to lexical scope (that is why you don't use them as methods in objects)
  - For regular functions: this gets bound to the object the method is invoked on

## How Node Works?
What happens when you start a Node.js app? It creates:
* 1 Process
  - This is the executing program (or part of it). Since Node.js has 1 process it is the whole executing program.
* 1 Thread
  - A basic unit to which OS allocates the process time (i.e., processor time)
* 1 Event Loop
  - continiously running Single-Threaded Loop - executes 1 command at a time
Node puts all (non-blocking) tasks into Event Loop
  - they are then passed to JS Engine and executed in order
I/O, Network Requests, Database Processes are qualified as blocking tasks in Node.js
  - This means that when Event Loop encounters them it sends them to a different Thread and moves to the next task in (Event-Loop) queue
  - ❗ A Thread is extracted from ThreadPool to handle each blocking task and when it is done, it puts the results in the **callback** queue
  - When the EventLoop finishes everything in the **events** queue it will start executing the tasks in callback queue

### NVM ###
[nvm](https://github.com/nvm-sh/nvm) & [nvm-windows](https://github.com/coreybutler/nvm-windows) for managing multiple versions of Node.js
* similar to virtual-env in Python - [article](https://www.sitepoint.com/quick-tip-multiple-versions-node-nvm/)
* [install on Ubuntu 14 ](https://www.liquidweb.com/kb/how-to-install-node-js-via-nvm-node-version-manager-on-ubuntu-14-04-lts/)
* [n - alternative to nvm](https://github.com/tj/n)

### Mono-Repos
- [storybook, lerna typescript combined](https://dev.to/shnydercom/monorepos-lerna-typescript-cra-and-storybook-combined-4hli)

### Event-Driven-Nature ###
Node's architecture is mostly asynchronous event-driven
- an important concept is [EventEmitter](https://medium.com/swlh/what-the-heck-is-an-event-emitter-84407fce6cd3)
  - in the article they provide the analogy with the Radio 📻
  - There is a radio-station which plays the content (event-emitter), and there are listeners of the radio (listeners for events)
- Node has built in module *Events* which implements EventEmitter
*[ARTICLE](https://jscomplete.com/learn/node-beyond-basics/node-events)*
- const emitter = new events.EventEmitter();
  - sidenote: listener must be created before the event is emitted
- Important: The same object actually both listens and emits events (like eventbus)
  - the new emitter will not be able to listen for the events made on first emitter

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
The child_processes module gives the node ability to spawn child processes by accessing OS commands
#### Worker Thread ####
* They present alternative to current Node.js approach (1 Process - 1 Thread - 1 Event Loop)
  - Worker Threads allow 1 Process (per app) with multiple Threads (where each Thread has 1 Event Loop)
* Fully Supported in Node.js 12
* [link to learn more](https://blog.logrocket.com/node-js-multithreading-what-are-worker-threads-and-why-do-they-matter-48ab102f8b10/)

### Streams ###
- Internally streams are pushing data in form of binary buffers
  - Streams are implementing event-emitters (they are working in such a way that they are listening and emitting events)
  - Streams are everywhere in Node.js
    - e.g., req,res in handleRequest in http (and express web server) are actually streams! These are called HttpStreams
      - HttpStreams are actually duplex streams (not separated req and res simplex streams)
- Simplex and Duplex Streams
  - Simplex are unidirectional streams: readable and writeable!
    - Readable stream is called "source" and writable stream is called sink
- Important point: read stream "produces" data which means that you can consume it
  - Important point it produces data by reading from datasource (Readable stream is pulling from datasource!, read stream is not the datasource itself!)
* [concat-stream](https://www.npmjs.com/package/concat-stream) - return a combined final result/output from the readable stream
  - it collects all data from stream and stores it as an object in memory
* [Node Streams - Everything you need to know](https://www.freecodecamp.org/news/node-js-streams-everything-you-need-to-know-c9141306be93/)
* [Node.js Streams Cheat Sheet](https://devhints.io/nodejs-stream)

- [Note from Substack's course on Streams] When using streams in Node.js, it is better to use library [*readablestreams*](https://github.com/nodejs/readable-stream) than *corestreams*
  - the reason is that core-stream tend to change their implementation so that API of this library can break your code
  - Apart from readablestreams you should also try library called *through2* (there are also from2 and to2)
    - NOTE: this library has method "this.push" which allows you to push chunk together with some previous chunks so that you can buffer them and process/send more data in one turn to the next stream
      - e.g., imagine case where you need to compress data, and there needs to be big enough buffer to compress data, or you want to stream data in chunks which are splitted by new line... in this case you would need to transform this data in some transform stream


### Functional-Programming ###
* Pure Functions
  - Deterministic: Produces always the same output for the same input
  - Does not produce side-effects
    - essentially it does not update some objects or makes some calls ...

## Other ##
1. [SO - **Remove** Node.js from windows](https://stackoverflow.com/questions/20711240/how-to-completely-remove-node-js-from-windows)
1. [npx](https://www.npmjs.com/package/npx) - runs the specified command from a certain package/binary
    - and if the package is not installed it will first install it
1. [Node script running forever](https://github.com/foreversd/forever)

### Issues ###
1. If you have the issue with node-sass
	- install node-sass version 4.12.0, and after that worked for me. npm install node-sass@4.12.0 --save
		- [Source of the answer SO](https://stackoverflow.com/questions/46515077/unable-to-install-node-sass-in-my-project/51530331#51530331)

1. npm fix: "Missing write access" [npm WSL](https://flaviocopes.com/npm-fix-missing-write-access-error/)
	- sudo chown -R $USER /usr/local/lib/node_modules
		- this command, I only had to remove /local from the directory path
	- that should solve problem of installing in WSL
sometime it helps to use "sudo"

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


## FunFacts ##
* Change color of Node.js console output
* Package-lock.json locks specific versions of projects
* WebAssembly in Node.js
* there is npm library "readme" which provides you with easy-accessible readme files of other packages (and works offline)
* New Features of JS language go through TC39 proposal process
  * There are 5 stages
  * after ES6, each new version of JS has the year in the name, i.e., ES2016, ES2017, ES2018

## Tutorials
* [Node.js - read large Files](https://itnext.io/using-node-js-to-read-really-really-large-files-pt-1-d2057fe76b33)
