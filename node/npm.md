1. [MISC](#Misc)
1. [About NPM dependencies](#Dependencies)
1. [Frequently used commands](#Frequently_used_commands)
1. [Useful NPM Modules](#Modules)
1. [NPM Semantic Versioning](#SemVer)

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
* [WinstonJS](https://github.com/winstonjs/winston) - Logger Manager for Node.js
* ❔ [node-static](https://www.npmjs.com/package/node-static) - File Server for serving static files
  - check also [node-static-alias](https://www.npmjs.com/package/node-static-alias)
* pm2 & forever - Process Managers to manage local development

### Express - Web Server ###
- Alternatives: Koa uses async/await “out of the box.” Express is callback-oriented.


### SemVer
- [NPM Semantic Versioning](https://docs.npmjs.com/about-semantic-versioning)
Scheme for Interface Versioning (for the benefit of the Interface Consumers)
- MAJOR.MINOR.PATCH (e.g., 0.3.10 comes before 0.10.3)
  - MAJOR - makes incompatible API Changes
  - MINOR - adds functionality in backwards-compatible manner
  - PATCH - adds backwards-compatible bug-fixes
    - [semver.org](https://semver.org/)
    - [NPM Semver Calculator](https://semver.npmjs.com/)
- SemVer can be specified as fixed version or as a range
- SemVer ranges are universally used by package authors to define what dependency versions they want their packages to be bundled with when installed
  - It exists so they can allow newer versions of packages to be installed automatically
    - Ranges can be specified explicitly with -,<,>,<=,>=
    - "*" - accepts any version, with default to latest
    - "2" (or 2.x.x.) covers all minor and patch versions less than *3*
    - "2.4" (or 2.4.x.) covers all patch versions less than *2.5*
  - Shorthand ranges ~(tilde) and ^(caret)
    - "*~*1.2.3" - range of acceptible versions that include all *patch* versions from the one specified up to, but not including the next *minor* version
      - "~1.2.3" => ">=1.2.3" & "<1.3.0"
    - "*^*1.2.3" - range of acceptible versions that include all *patch and minor* versions from the one specified up to, but not including the next *major* version
      - "^1.2.3" => ">=1.2.3" & "<2.0.0"
    - ^ is the default "npm install --save" prefix
- [SO - Diff between tilde and caret in npm semver](https://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json)
