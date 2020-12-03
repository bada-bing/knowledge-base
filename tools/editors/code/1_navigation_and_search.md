Consider Improving your Keyboard Shortcuts for switching between Editor and Terminal
and addtionally on switching between different tabs in the terminal
- additionally set WT as default external Terminal:
https://offering.solutions/blog/articles/2020/03/24/setting-windows-terminal-as-default-external-terminal-in-visual-studio-code/


# Essential Navigation
## Omnibox - Fuzzy File Navigation (Ctrl + p)
  - `Ctrl + Enter` (instead of `Enter`) will open the File in the Side Window

## Command Palette (shift+ctrl+p)
- `F1` works in the same way as `ctrl + shift + p` (Opens Command Palette)
- `@` opens symbol browser (for that file)
  - Symbol Search is used for Function & Classes Names, rules, ...
- `@:` groups symbols into related segments (e.g., classes, methods, functions)
- `#` cross-search (across different files throughout the whole project, workspace)
- `:` to go directly to a specific line.

## Navigation Moving and Line Management
You don't need to highlight a WHOLE line in VS Code to cut it (or copy it)
- it is enough to press `Ctrl + C` (or `Ctrl + X`)
- It works the same way in **IntelliJ**

## Code Navigation - Go To
- hold CTRL and when you click on something it will lead you to where it is defined
- same holds for Go To Definition and Peek Definition
- especially that it opens this inline browser, which you can even use to edit directly the content (not only to see "the related code")

# Search
- ⭐ use regex to search
  - use `ALT + ENTER` to select all occurences

- switch between open side editors using (Ctrl + 1; Ctrl + 2)
  - editor is NOT a tab (editor is like pane in tmux)

  - ```code -r ``` opens the code in the last recently used environment

- [Preview Editors](https://github.com/Microsoft/vscode-docs/blob/vnext/release-notes/June_2016.md#preview-editors)
  - Files with *Tab Title written in Italics*
    - if open new file from this tab, the new opened file will overwrite the existing content of that tab
    - if you double-click on the tab name the file goes from `Preview` to `Open Mode` (the italics letter will become normal)
