Still need to check:
https://medium.com/productivedev/toward-a-mouse-free-developer-experience-in-vscode-97e621d5136e
https://medium.com/better-programming/20-vs-code-shortcuts-for-fast-coding-cheatsheet-10b0e72fd5d
https://jsmanifest.com/21-vscode-shortcuts-to-code-faster-and-funner/
https://dev.to/lampewebdev/my-web-development-vs-code-settings-theme-extensions-tips-and-tricks-1324
https://github.com/30-seconds/30-seconds-of-code [Snippets]
https://www.barbarianmeetscoding.com/blog/2019/02/08/boost-your-coding-fu-with-vscode-and-vim

In VS Code I covered most of the article … I came to code [formatting](https://github.com/microsoft/vscode-tips-and-tricks#code-formatting)

- [customize](./code.customize.md)
- [linting](./code.linting.md.md)
- [debugging](#debugging)

# Tips
- In terminal you can write:
  - ```code --diff <file1> <file2>``` to activate code's diff-checker editor
    - in GUI: in File Explorer -> right click on the file -> "select for compare" and "compare with selected"
    - or select 2 files and "compare selected"
  - ```code -r ``` opens the code in the last recently used environment
- In a similar way you can create bash-functions to import and export extensions:
  - Bash script to export & import extensions
  	- vscode_export() { code --list-extensions }
  	- vscode_import() { cat "$1" | xargs -L 1 code --install-extension }
- A lot of Git commands are available in VS Code (e.g., merge branch)

- Use F8 to Cycle through Problems
  - You can filter problems by type ('errors', 'warnings') or text matching

- Fuzzy File Navigation (Ctrl + p) - Omnibox
  - When you write the name of the File and press Ctrl + Enter, it will open the File in the Side Window (for Side-by-side Editing)
    - then you can switch between open side editors using (Ctrl + 1; Ctrl + 2)
  - By adding ":", you can go directly to a specific line.
  - Symbol navigation: By adding "@:", you can activate Symbol Search (for that file).
    - Symbol Search is used for Function & Classes Names, rules, ...
  - Symbol navigation: By adding "#", you can activate Symbol Search throughout the whole project (workspace).
- F1 works in the same way as ctrl + shift + p (Opens Command Palette)

In Settings you can create File Associations for File Extensions that are not detected accurately (for example, many config files are in JSON):
```json
"file. associations" : {
 ".database" : "json"
 }
```
Create language associations for files that aren't detected accurately (for example, many config files are JSON).

- [How to integrate git-bash](https://dev.to/simbo1905/how-to-integrate-git-bash-with-visual-studio-code-on-windows-3217)


# Facts
Both VS Code and Chrome DEV Tools have **Logpoints** (apart from Breakpoints and Conditional Breakpoints)
- they behave like "console.log" but you don't need to insert them into the code
  - you can place them like the regular bookmark (you just need to select the line and make a right click and too choose Logpoint)
- since they do not work if there is a syntax error, I am not sure if they are useful
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
# Shortcuts

| Command                    |                                      Description |
| -------------------------- | -----------------------------------------------: |
| alt + shift + j            |     Join selected lines (my own custom shortcut) |
| ctrl + alt + up/down arrow |            Add Cursor for Multi-Cursor Selection |
| shift + ctrl + ö           |                          Activate (New) Terminal |
| ctrl + j                   | Open Terminal Panel (Does not open new terminal) |
| ctrl + backspace           |                               Deletes whole word |
| ctrl + k -> z              |                                         Zen Mode |
| ctrl + k -> f              |       Close current Workspace (Folder Structure) |
| ctrl + shift + f           |                                Search Everywhere |
| Ctrl + r                   |                                    Reload Window |
| Ctrl + 1/2/3               |                     Switch between Editors/Panes |
| Alt + 1/2/3                |                             Switch between Files |
| ctrl + PG UP/DOWN          |                    Move through Open Editor Tabs |
| ctrl + F -> Alt + Enter    |                      select all found occurences |
| Ctrl + Shift + V           |                                 Preview Markdown |
| Ctrl + Shift + Space       |                       Preview Function Signature |

### Moving and Line Management
You don't need to highlight a WHOLE line in VS Code to cut it (or copy it)
	- it is enough to press Ctrl + C (or Ctrl + X)
	- It works the same way in **IntelliJ**


| Command                     |          Description |
| --------------------------- | -------------------: |
| alt + up/down arrow         |           move lines |
| alt + shift + up/down arrow |            copy line |
| ctrl + shift + k            |          delete line |
| ctrl + l                    |          select line |
| alt + shift + left/right    |     Expand Selection |
| ctrl + u                    | Undo Cursor Position |

### Code & Development
| Command   |      Description |
| --------- | ---------------: |
| F12       | Go to Definition |
| Alt + F12 |  Peek Definition |


# Debugging
https://scotch.io/tutorials/debugging-javascript-in-google-chrome-and-visual-studio-code
https://vuejs.org/v2/cookbook/debugging-in-vscode.html
https://github.com/microsoft/vscode-recipes/tree/master/vuejs-cli
