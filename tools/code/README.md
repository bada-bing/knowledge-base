# ToC
* [Navigation and Search](1_navigation_and_search.md)
* [Development](2_development.md)
* [Text Manipulation](3_text-manipulation.md)
* [Linting](linting.md)
* [Customization](customize.md)

- shortcuts file should be dissolved into other files
⭐ So many shortcuts, that this is not useful, I will reorganize this
  - cluster into the features like (code navigation, text manipulation, debugging) and I will there both put tips and shortcuts ⭐


What do I care about:
1. Features
2. Shortcuts (customize to fit to features you use)
3. Extensions (don't use what you don't need; don't be affraid to try new things)

# Courses
* [VS Code - Mike North](https://frontendmasters.com/courses/visual-studio-code/)
  - [Course Outline and Slides - GitHub Repo](https://github.com/mike-works/vscode-fundamentals)
* [VS Code can do that - Burke Holland](https://frontendmasters.com/courses/customize-vs-code/)
  - [GitHub Repo](https://github.com/burkeholland/workshop-vs-code-can-do-that)

* In VS Code I covered most of the article … I came to code [formatting](https://github.com/microsoft/vscode-tips-and-tricks#code-formatting)
- [customize](./code/customize.md)
- [navigation](./code/1_navigation.md)
- [linting](./code/linting.md.md)
- [debugging](#debugging)

# Features
- code's diff-checker editor - CLI: ```code --diff <file1> <file2>``` -
  - in GUI: in File Explorer -> right click on the file -> `select for compare` and `compare with selected`
  - or select 2 files and `compare selected`

- Omnibox - Fuzzy File Navigation (Ctrl + p)
  - `Ctrl + Enter` (instead of `Enter`) will open the File in the Side Window
- `F1` works in the same way as `ctrl + shift + p` (Opens Command Palette)

- switch between open side editors using (Ctrl + 1; Ctrl + 2)
  - editor is NOT a tab (editor is like pane in tmux)

  - ```code -r ``` opens the code in the last recently used environment

- [Preview Editors](https://github.com/Microsoft/vscode-docs/blob/vnext/release-notes/June_2016.md#preview-editors)
  - Files with *Tab Title written in Italics*
    - if open new file from this tab, the new opened file will overwrite the existing content of that tab
    - if you double-click on the tab name the file goes from `Preview` to `Open Mode` (the italics letter will become normal)

- VS Codelens - They're interactions that allow context aware actions for portions of your code base.

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

## Tasks
- what is especially useful is that you can capture output into "problems" and make them a clickable links
  - here is the link from slides [link](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/2_customizing/tasks.md)
    - an example where this could be useful is if you run prettier and try to lint the code and to make as clickable links all the warnings and errors

# Data
- `Cosmos DB` extension to communicate to Mongo DB (Cosmos DB is related to Azure, but it can work for any Mongo DB)
