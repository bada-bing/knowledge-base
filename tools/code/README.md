Still need to check:
https://medium.com/productivedev/toward-a-mouse-free-developer-experience-in-vscode-97e621d5136e
https://code.visualstudio.com/blogs/2018/07/12/introducing-logpoints-and-auto-attach

# Courses
## VS Code - Mike North
[VS Code - Mike North](https://frontendmasters.com/courses/visual-studio-code/)
[Course Outline and Slides - GitHub Repo](https://github.com/mike-works/vscode-fundamentals)
visual-studio-code

## VS Code can do that - Burke Holland #
[Link to the Course](https://frontendmasters.com/courses/customize-vs-code/)
  - ⭐[Website - GitBook](https://burkeholland.gitbook.io/vs-code-can-do-that/)
    - take a look how he created his gitbook for useful exmaples
  - [GitHub Repo](https://github.com/burkeholland/workshop-vs-code-can-do-that)
  - [Extension Plugin Bundle](https://marketplace.visualstudio.com/items?itemName=burkeholland.vs-code-can-do-that)


In VS Code I covered most of the article … I came to code [formatting](https://github.com/microsoft/vscode-tips-and-tricks#code-formatting)
- [customize](./code.customize.md)
- [shortcuts](./code.shortcuts.md)
- [linting](./code.linting.md.md)
- [debugging](#debugging)

# Tips
- CLI Commands:
  - ```code --diff <file1> <file2>``` - code's diff-checker editor
    - in GUI: in File Explorer -> right click on the file -> `select for compare` and `compare with selected`
    - or select 2 files and `compare selected`
  - ```code -r ``` opens the code in the last recently used environment

- Use `F8` to Cycle through Problems
  - You can filter problems by type ('errors', 'warnings') or text matching

- Fuzzy File Navigation (Ctrl + p) - Omnibox
  - `Ctrl + Enter` (instead of `Enter`) will open the File in the Side Window
  - switch between open side editors using (Ctrl + 1; Ctrl + 2)
    - editor is NOT a tab (editor is like pane in tmux)
  - In command-palette `:` to go directly to a specific line.
  - Symbol navigation: By adding "@:", you can activate Symbol Search (for that file).
    - Symbol Search is used for Function & Classes Names, rules, ...
  - Symbol navigation: By adding "#", you can activate Symbol Search throughout the whole project (workspace).
- F1 works in the same way as ctrl + shift + p (Opens Command Palette)

- In Settings you can create language associations for File Extensions that are not detected accurately (eg, many config files are in JSON):
```json
"file. associations" : {
 ".database" : "json"
 }
```

- [Preview Editors](https://github.com/Microsoft/vscode-docs/blob/vnext/release-notes/June_2016.md#preview-editors)
  - Files with *Tab Title written in Italics*
    - if open new file from this tab, the new opened file will overwrite the existing content of that tab
    - if you double-click on the tab name the file goes from Preview to Open Mode (the italics letter will become normal)
- VS Code uses Emmet
  - Emmet is inteligent enough to read data aobut the size of the image and to populate attributes width and height automatically
		- it is important to set this attributes in advance so that browser knows immediately how much space to reserve for the image
    - By using updateImageSize in command in VS Code, emmet can find the source of the image and automatically populate these attributes
- Workspace specific files are in .vscode. For example, tasks.json for the Task Runner and launch.json for the debugger.
- VS Codelens - They're interactions that allow context aware actions for portions of your code base.

- ⬇ Both VS Code and Chrome DEV Tools have **Logpoints** (apart from Breakpoints and Conditional Breakpoints)
  - they behave like `console.log`, but they belong to the Editor itself and are never inserted into the source code.
  - they do NOT work if there is a syntax error, and therefore are NOT that useful.

## Navigation Moving and Line Management
You don't need to highlight a WHOLE line in VS Code to cut it (or copy it)
- it is enough to press `Ctrl + C` (or `Ctrl + X`)
- It works the same way in **IntelliJ**

## Search
- ⭐ use regex to search
  - use `ALT + ENTER` to select all occurences

- `@` opens symbol browser
- `@:` groups symbols into related segments (e.g., classes, methods, functions)
- `#` cross-search (across different files)

## Go To
- hold CTRL and when you click on something it will lead you to where it is defined
- same holds for Go To Definition and Peek Definition
- especially that it opens this inline browser, which you can even use to edit directly the content (not only to see "the related code")

## Emmet
|              Tip & What is about               |                                                                 Section                                                                 |
| :--------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------: |
|      Find the process using specific port      |                                                           VS Code can do that                                                           |
|                Emmet Shortcuts                 | [Creating HTML with Emmet](https://burkeholland.gitbook.io/vs-code-can-do-that/exercise-2-productivity-tricks/creating-html-with-emmet) |
|          Code/HTML Folding By Region           |                                                        \\#region & \\#endregion                                                         |
| Debugging Applications within Docker Container |                [Debugging Docker Containers](https://burkeholland.gitbook.io/vs-code-can-do-that/exercise-5-docker/debugging-docker-containers)                |

|                  Action                   |     Shortcut     |
| :---------------------------------------: | :--------------: |
| Check Build Tasks for the associated File | Ctrl + Shift + B |

Emmet is aware of the context you are in
- by default it will give you `div`, but if you are inside of `ul` it will give you `li` by default

some emmet abbreviations
! (and TAB) gives you basic HTML page template

sometimes if you write long expressions, emmet can get lost - in that cases you should press SPACE + ENTER to bring emmet back

⭐ Emmet has functionality `balance inward` & `balance outward`
  - it balances your selection (of code) to the closing tags (this is like in intellij IDEA when you press multiple times CTRL + W) - it expands your selection in a smart way
⭐ `Wrap with abbreviation` - this will wrap the selection with `emmet abbreviation` (e.g., `div`)
⭐ `Update Tag` - can be used to replace opening and closing tags, e.g., from div to selection
⭐ `Update Image Size` - you should always specify image size (so that browser knows how much space to reserve)
- emmet can do this for you

- think of it as using CSS Selectors for DOM generation
- emmet is a nice feature, aim to use it! (and don't be obsessed with productivity) like in regex... better to use many small emmet patterns than one which is big
  - also, vs code usually places cursors in right spots, so that helps as well
- 🌟if I understood correctly when typing abreviations, you should not use spaces anywhere!
- "+" sibling selector `.navbar + .content + .footer`
- ">" direct descendant selector `ul > .list-items*5{Item $}`
  - it will create 5 li items with content "Item 1", ... $ represents index
  - it already knows that inside of ul children should be of type `li`

# Debugging
https://scotch.io/tutorials/debugging-javascript-in-google-chrome-and-visual-studio-code
https://vuejs.org/v2/cookbook/debugging-in-vscode.html
https://github.com/microsoft/vscode-recipes/tree/master/vuejs-cli

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

nodemon has also default configuration for debugging in VS Code
- it is available as one of default options when you setup `launch.json`

- there are compound configurations (to debug both backend and frontend at the same time) but do not find them that useful right now
    - if you feel the need at some point, invest more time into it, for now just skip it
    - in launch.json you would specify something like `"compounds": [...]`

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


for work with containers VS Code has remote-containers
- essentially this is about having the application running from the container, but being integrated with your VS Code
- it opens the project from the container (and also VS Code is part of that container, it will have all settings which are stored in .devcontainers configuration)
  - we can use that containerized VS Code (with the project) as our development environment
  - how this works is that VS Code sets up a little server in the container which communicates with our VS Code and they are able to share information
- configuration for this is in .devcontainers folder

# Git & Source-Control
## inline annotations to show differences from your local changes
- each new line which is changed, i.e., different from content commited in Repository will be marked with "some blue marker" next to the line number
- if the content is removed we see in a similar way the red triangle which denotes that something is removed
- if the content is added it will show green indicator
- the indicator in the bottom-bar next to the branch name is the sync-indicator (it does both pull and push, and that is the main difference to "just pull")
- in vscode is really simple to undo last commit
- in Source Control window just find option "undo last commit"

- similar like in SourceTree, you can also stage only chunks of a certain file
  - in GIT view select part of the file which you want to stage and right-click it
    - select "stage selected ranges" (there are options to revert and untrack)

Github has an official extension for working with Pull Requests in VS Code

# Data
Burke Holland uses Cosmos DB extension to communicate to Mongo DB (Cosmos DB is related to Azure, but it can work for any Mongo DB)


## Tasks
- what is the benefit of running tasks? convenience?
  - it looks like that you can run npm scripts as tasks
    - shift + ctrl + p > type "task"
- what is especially useful is that you can capture output into "problems" and make them a clickable links
  - here is the link from slides [link](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/2_customizing/tasks.md)
    - an example where this could be useful is if you run prettier and try to lint the code and to make as clickable links all the warnings and errors


## Markdown
- [slides](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/1_using/markdown.md)
- you can use img tags (like in html) and give them a lot of options
  `<img src="vscode_icon.png" height=50 align=right vspace=20 />`
- align attribute can be used on variety of HTML tags
- `<p align=right>hello</p>`
### details
```markdown
<details>
  <summary>Click me for something crazy</summary>

  The content which is hidden
  ```ts
  let Hello: string = "World";
  ```
</details>
```
### description lists
```markdown
<dl>
  <dt>Images</dt>
  <dd>.jpg, .gif, .png</dd>
  <dt>Styles</dt>
  <dd>.css</dd>
</dl>
```
