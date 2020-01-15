1. [MISC](#Misc)
1. [About NPM dependencies](#Dependencies)
1. [Frequently used commands](#Frequently_used_commands)
1. [Useful NPM Modules](#Modules)

## Misc ##
Sometimes in npm scripts (also saw it in webpack config) you need to pass arguments like "-- --arg1 val1"
- the initial "--" signifies the end of the command operation and beginning of positional parameters


## Dependencies ##
[Article: Understanding NPM Dependency Model](https://lexi-lambda.github.io/blog/2016/08/24/understanding-the-npm-dependency-model/)
- SemVer versioning Scheme: packages depend on other packages, and these dependencies are expressed with *version ranges*
  - sidenote: packages depend on ranges rather on specific versions
- NPM handles dependencies as *tree of dependencies*
  - this means that every installed package get its own set of dependencies (they are not sharing the same canonical set of packages)
  - additionally, npm 3 does optimizations in an attempt to share dependencies where it can
- essentially, if one package is required in different versions, it will be installed multiple times (in all required versions)
- peer dependency: [STILL NOT CLEAR ENOUGH - DO MORE RESEARCH]
  - rather than getting its own copy of a dependency, a package expects that dependency to be provided by its dependent
    - this means, that in that case there is one canonical version which satisfies everyone's constraint
  - if the export function returns something which depends on certain dependency, then you need to list it as a peer dependency
    - FIND THIS IN THE ARTICLE, it is better explained -> SEARCH FOR "createSquareJpeg"
- READ THIS [SO - What is diff between dependencies, devDependencies and peerDependencies](https://stackoverflow.com/questions/18875674/whats-the-difference-between-dependencies-devdependencies-and-peerdependencies)

### Frequently_used_commands ###
npm list -g --depth=0
	- check the globally installed package version

npm link
	- https://medium.com/dailyjs/how-to-use-npm-link-7375b6219557


## Modules ##
* https://github.com/nock/nock
	- Mock HTTP server (for mocking responses)
* Puppeeter and Chrome in Node.js
* Web Scraper - node-osmosis
* Backpack - minimalistic build system for Node.js
* [strong-pm.io/](http://strong-pm.io/) - Process Manager for Node.js

### Express - Web Server ###
- Alternatives: Koa uses async/await “out of the box.” Express is callback-oriented.
