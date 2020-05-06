# VS Code - Mike North
[VS Code - Mike North](https://frontendmasters.com/courses/visual-studio-code/)
[Course Outline and Slides - GitHub Repo](https://github.com/mike-works/vscode-fundamentals)
visual-studio-code

## Mardown
- [slides](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/1_using/markdown.md)
- you can use img tags (like in html) and give them a lot of options
  `<img src="2020-04-23-20-06-30.png" height=50 align=right vspace=20 />`
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

## Emmet
- think of it as using CSS Selectors for DOM generation
- emmet is a nice feature, aim to use it! (and don't be obsessed with productivity) like in regex... better to use many small emmet patterns than one which is big
  - also, vs code usually places cursors in right spots, so that helps as well
- 🌟if I understood correctly when typing abreviations, you should not use spaces anywhere!
- "+" sibling selector `.navbar + .content + .footer`
- ">" direct descendant selector `ul > .list-items*5{Item $}`
  - it will create 5 li items with content "Item 1", ... $ represents index
  - it already knows that inside of ul children should be of type `li`

## Go To
- hold CTRL and when you click on something it will lead you to where it is defined
- it looks like that I wasn't really using this feature, but it is extremly useful
- same holds for Go To Definition and Peek Definition
  - especially that it opens this inline browser, which you can even use to edit directly the content (not only to see "the related code")

- probably the next thing you should learn in VS Code is multi-cursor and how that works

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
  - JSDoc has many features, probably many of them you can do with TypeScript, so don't bother too much using JSDoc for type definitions
    - on the other hand it can be useful to check what other features have JSDoc in order to write good comments
      - e.g., `@see`
- Important constructors are regarded as types!
- VS Code uses structural type system (not nominal)
  - that means that it will induce the type based on the structure of the object (if it has properties relevant for that type) ... if it walks like a duck, and makes noise like a duck, it is a duck
  - nominal type system would mean that it will induce the type based on the name (I think that is how Java works)

## Debugging
- debugging of node in VS Code is based on `node --inspect --inspect-brk ./index.js`
  - inspector is a new node debugging protocol (to enable different tools to communicate with node)
  - there are 2 options (launch to inspect new session or attach to inspect existing session)
  - Invest more in learning conditional breakpoints and other features (e.g, there is a hit-count, that is ... it will break (freeze)  only if that line is accessed that number of times)
  - Restart Frame is a good feature (you specify a stackframe (i.e., function) in the stack trace, and click "restart frame" and it will restart everything and stop at that point)
    - it can be helpful in situation where you need to make api calls or restart browser, it can help you there a lot, so research
  - skipping code (this feature exists in Chrome as well)
    - this is really helpful since you don't want to bother with native libraries and stop there at any point (e.g., Vue lib)
  - launch.json is the file in .vscode where you specify your debug configuration


## Customization
- Levels of Customization
  - Workspace ./.vscode/settings.json
  - User %APPDATA\Code\User\Settings.json (Windows)
  - User $HOME/.config/Code/User/Settings.json (Windows)
  - Defaults that ship with editor
  - you can edit user and workspace settings using CTRL + , (there are different tabs for user and workspace settings)
- pro tip: don't install many fonts (they all take space in the ram (all the time) - there is table with fonts which is loaded into ram)
- you should start creating user snippets (and invest time learning ones which you already know)

## Tasks
- what is the benefit of running tasks? convenience?
  - it looks like that you can run npm scripts as tasks
    - shift + ctrl + p > type "task"
- what is especially useful is that you can capture output into "problems" and make them a clickable links
  - here is the link from slides [link](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/2_customizing/tasks.md)
    - an example where this could be useful is if you run prettier and try to lint the code and to make as clickable links all the warnings and errors

https://csstriggers.com/ - here you can see how big impact has a different css property on browser (does it need to do a recomposition, a repainting, or rerendering)
- there is a similar extension for vs code, which gives you a visual queues how expensive is a certain css property

# VS Code can do that - Burke Holland #
[Link to the Course](https://frontendmasters.com/courses/customize-vs-code/)
  - ⭐[Website - GitBook](https://burkeholland.gitbook.io/vs-code-can-do-that/)
    - take a look how he created his gitbook for useful exmaples
  - [GitHub Repo](https://github.com/burkeholland/workshop-vs-code-can-do-that)
  - [Extension Plugin Bundle](https://marketplace.visualstudio.com/items?itemName=burkeholland.vs-code-can-do-that)

Settings (UI) - in the background uses Azure's AI (when connected to the Internet)
- this mean that it will give it best to interpret your query and guess what you really want

F8 keyboard shortcut - cycle through problems

- you should create workspace folder for your cart-ui project so that it distinguishes frontend and bff as separate projects

## List of Tweaks for VS Code (in Settings.json)
- Turn off the Minimap
- Move Sidebar Right
- Hide Open Editors

|                 Action                  |       Shortcut        |
| :-------------------------------------: | :-------------------: |
|             Toggle Sidebar              |        Ctrl+B         |
|         Jumpt to Previous File          |     Ctrl + P -> P     |
|          Set Focus to Sidebar           |       Ctrl + 0        |
|           Set Focus to Editor           |       Ctrl + 1        |
|           Open Explorer View            |   Ctrl + Shift + E    |
|             Open Debug View             |   Ctrl + Shift + D    |
| Fold HTML/Code (*does not work always*) |   Ctrl + Shift + ß    |
|          Comment out the Line           |        Ctrl+#         |
|             Symbol Browser              | Ctrl+P -> insert "@"  |
|        Groupped Symbols Browser         | Ctrl+P -> insert "@:" |
|              Code Actions               |        Ctrl+.         |
|       See Available Code Actions        |   Ctrl + Shift + R    |

|    (Multiple Cursors) Action    |    Shortcut     |
| :-----------------------------: | :-------------: |
|         Add new Cursor          |     Ctrl+D      |
|        Skip one Instance        |  Ctrl+ K -> D   |
|      Select all Instances       | Ctrl+ Shift + L |
| ⭐(Peak into) See all References |   Shift + F12   |


---

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


## Settings
npm script explorer > set it to true to enable npm scripts in your file explorer sidebar

## VS Code Navigation
multiple cursors CTRL + D
- if you want to skip one occurence CTRL + K

Search
- you can also use regex to search
- when it finds multiple matches you can use ALT + ENTER to select all occurences

"@" opens symbol browser
"@:" groups symbols into related segments (e.g., classes, methods, functions)
"#" - cross-search (across different files)


CTRL - 0 - go to sidebar (so that you can move there)
CTRL - 1 - go to the editor

CTRL + P > CTRL + P - will bring you back to previous file

there is a setting `javascript.implicitProjectConfig.checkJs` - this will check your JS (like TS) files (it is like setting `//@ts-check` on every js file)

vscode can for different projects hide/exclude certain files
- e.g., if you are not interested in node modules you can hide that
- in settings.json you add something like
```json
{
  "files.exclude": {
    "**/*.js": true
  }
}
```

for launch configuration you can store your env variable into .env file
and then specify the file in launch config using `envFile`: ...

nodemon has also default configuration for debugging in VS Code
- search for it when you setup launch.json

- there are compound configurations (to debug both backend and frontend at the same time) but do not find them that useful right now
    - if you feel the need at some point, invest more time into it, for now just skip it
    - in launch.json you would specify something like `"compounds": [...]`
-

https://code.visualstudio.com/blogs/2018/07/12/introducing-logpoints-and-auto-attach

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

# Data
Burke Holland uses Cosmos DB extension to communicate to Mongo DB (Cosmos DB is related to Azure, but it can work for any Mongo DB)

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
