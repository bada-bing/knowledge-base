# Debugging
[how to attach vscode to debugger](https://code.visualstudio.com/blogs/2018/07/12/introducing-logpoints-and-auto-attach)
https://scotch.io/tutorials/debugging-javascript-in-google-chrome-and-visual-studio-code
https://vuejs.org/v2/cookbook/debugging-in-vscode.html
https://github.com/microsoft/vscode-recipes/tree/master/vuejs-cli

- Use `F8` to Cycle through Problems
  - You can filter problems by type ('errors', 'warnings') or text matching

- debugging of node in VS Code is based on `node --inspect --inspect-brk ./index.js`
  - inspector is a new node debugging protocol (to enable different tools to communicate with node)
  - there are 2 options (launch to inspect new session or attach to inspect existing session)
  - Invest more in learning conditional breakpoints and other features (e.g, there is a hit-count, that is ... it will break (freeze)  only if that line is accessed that number of times)
  - Restart Frame is a good feature (you specify a stackframe (i.e., function) in the stack trace, and click "restart frame" and it will restart everything and stop at that point)
    - it can be helpful in situation where you need to make api calls or restart browser, it can help you there a lot, so research
  - skipping code (this feature exists in Chrome as well)
    - this is really helpful since you don't want to bother with native libraries and stop there at any point (e.g., Vue lib)
  - launch.json is the file in .vscode where you specify your debug configuration

- for launch configuration store your env variable into `.env` file and then specify the file in launch config using `envFile`

- `nodemon` has also default configuration for debugging in VS Code
  - it is available as one of default options when you setup `launch.json`

- ⬇ `compound configurations` - multiple launch configurations at the same time (e.g., debug both backend and frontend at the same time)
  -  I do not find it that useful right now
    - in launch.json you would specify something like `"compounds": [...]`

- ⬇ Both VS Code and Chrome DEV Tools have **Logpoints** (apart from Breakpoints and Conditional Breakpoints)
  - they behave like `console.log`, but they belong to the Editor itself and are never inserted into the source code.
  - they do NOT work if there is a syntax error, and therefore are NOT that useful.

## Type Checking
- use types wherever you can
- they help you to catch bugs at compile time! (this should highly increase maintainability of the project)
- and better dev experience (it provides better autocompletion and additionally serves a documentation)
  - some functions are less amigiuous when you add types
    - e.g., function add could mean something different if your parameters are of type number, or of type array
- TS files are automatically checked in VS Code
  - if you have **tsconfig.json** in your project, you can add `"checkJs":true` to also check JS files
  - otherwise, no matter which type of project is, you can add `// @ts-check` on top of the file to enable type checking for that file
- additionally, you can add types using comment annotations with JSDoc:
```javascript
/** @type{number} */
let value;
```

- VS Code uses structural type system (not nominal)
  - that means that it will induce the type based on the structure of the object (if it has properties relevant for that type) ... if it walks like a duck, and makes noise like a duck, it is a duck
  - nominal type system would mean that it will induce the type based on the name (I think that is how Java works)

# Dockerizing an Application
- we dockerize the application (e.g., express app) so that we can ship it and run it somewhere else
- First step which you need to do is to add configuration files
  - Dockerfile, docker-compose.yml, docker-compose.debug.yml, and .dockerignore
  - Open COmmand Palette and run "Docker: Add Docker Files to Workspace"
    - then select the app platform (e.g., node) and it will pull base image (from dockerhub) for that platform
  - Dockerfile is used to build the image, and if you want to build it, you will run `docker: build image`
    - check what does really build image means? is it building a container from image or building an image
  - for runnning containers you can attach to them using attach shell or you can view logs
- you can use VS Code to deploy to a docker registry (dockerhub)

- docker-compose.yml allows you to specify multiple images and link them together
  - e.g., enables our containerized app to talk to mongodb (which is also a container)

- docker-compose.debug.yml can be used to debug your app which is running inside of a container

for work with containers VS Code has `remote-containers`
- essentially this is about having the application running from the container, but being integrated with your VS Code
- it opens the project from the container (and also VS Code is part of that container, it will have all settings which are stored in .devcontainers configuration)
  - we can use that containerized VS Code (with the project) as our development environment
  - how this works is that VS Code sets up a little server in the container which communicates with our VS Code and they are able to share information
- configuration for this is in .devcontainers folder


# Shortcuts
## Code & Development
| Command            |       Description |
| ------------------ | ----------------: |
| F12                |  Go to Definition |
| Alt + F12          |   Peek Definition |
| `Ctrl + Shift + ß` |   1. Code Folding |
| `Ctrl + Shift + ´` | 2. Code Unfolding |
