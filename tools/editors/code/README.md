# ToC
* [Features](#features)
* [Customization](customize.md)
- [Shortcuts](./shortcuts.md) - should be dissolved into other files based on the features

What are my main Use-Cases:
1. Development
   * Testing
2. Writing Documentation

Requirements:
1. Speed
   1. Being Mouseless
2. Automatization
   1. Delegation of tasks to the tool (e.g., linting, formatting, text insertion)
   2. this is directly related to integration with other tools (e.g, linting tools, docker,...)
3. Having Disposable Environments
   - Similar to other tools, it needs to be *disposable* (ie, it needs to work out of the box)
     - settings should be synced
     - where useful and applicable I should have the isolated environments (running environment together with the source code, e.g., node.js, java, mongo, zk)
   - two relevant features: `Remote Containers` ans `Sync` functionality
4. Nice UI

How can the tool help me to satisfy the requirements:
1. Features
   - important Keybindings and Tips for the available Features
2. Customization (what would be relation between extensions and customization, and customization and shortcuts)
   1. Extensions (don't use what you don't need; don't be affraid to try new things)
   2. Settings & Keybindings

What can I do about it?
1. I will not hesitate to try new tools, extensions, features and make research about new stuff
2. I will keep my documentation up-to-date and my customization settings syncronized
3. I will use only what I need (will try hard not to overengineer, and use only extensions which I really need)
4. I will optimize the tool and its usage to my needs, and not vice versa.

# Features
* [Navigation and Search](1_navigation_and_search.md)
* [Development](2_development.md)
* [Text Manipulation](3_text-manipulation.md)
- VS Codelens - They're interactions that allow context aware actions for portions of your code base.
* [Source-Control](4_source_control.md)
* [Linting](linting.md)
* [Automatization](#automatization)
* [Data Management](#data)

# Automatization
## Tasks
- what is especially useful is that you can capture output into "problems" and make them a clickable links
  - here is the link from slides [link](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/2_customizing/tasks.md)
    - an example where this could be useful is if you run prettier and try to lint the code and to make as clickable links all the warnings and errors

# Data
- `Cosmos DB` extension to communicate to Mongo DB (Cosmos DB is related to Azure, but it can work for any Mongo DB)

## Courses
* [VS Code - Mike North](https://frontendmasters.com/courses/visual-studio-code/)
  - [Course Outline and Slides - GitHub Repo](https://github.com/mike-works/vscode-fundamentals)
* [VS Code can do that - Burke Holland](https://frontendmasters.com/courses/customize-vs-code/)
  - [GitHub Repo](https://github.com/burkeholland/workshop-vs-code-can-do-that)

* In VS Code I covered most of the article … I came to code [formatting](https://github.com/microsoft/vscode-tips-and-tricks#code-formatting)
- [customize](./code/customize.md)
- [navigation](./code/1_navigation.md)
- [linting](./code/linting.md.md)
- [debugging](#debugging)


You can easily create a sub-folder from an already existing file. To do this, select a file and click on rename. Then, add a backslash (/) at the point you need it to be demarcated from.

E.g. To create a bio sub-folder from authorbio.js, type author/bio.js

`$ZSH_CUSTOM` - the path to custom_plugins
