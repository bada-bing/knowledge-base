Community curated extension lists, such as [awesome-vscode](https://github.com/viatsko/awesome-vscode)

# Main Principle:
  1. Do not fear to try new stuff and even break something
  2. Make it as simple as possible (do not use what you don't need)

## What to Consider when Customizing:
- Theme: One Dark Pro
  - alternative: [Dracula](https://marketplace.visualstudio.com/items?itemName=dracula-theme.theme-dracula)
- Icons Theme: [Material Icons Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
- Font: Fira Code (with ligatures)
  - In settings.json:
	- ```"editor.fontFamily": "Fira Code", "editor.fontLigatures": true```
	- font size to **15**
- Keyboard Shortcuts
- Tune your settings (settings.json)
- ❔ Add JSON validation
- Create snippets
- Install extensions

## Customization
- Levels of Customization
  - Workspace ./.vscode/settings.json - [Workspace Customization](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/2_customizing/workspace.md)
  - User %APPDATA\Code\User\Settings.json (Windows)
  - User $HOME/.config/Code/User/Settings.json (Windows)
  - Defaults that ship with editor
  - you can edit user and workspace settings using CTRL + , (there are different tabs for user and workspace settings)
- pro tip: don't install many fonts (they all take space in the ram (all the time) - there is table with fonts which is loaded into ram)
- you should start creating user snippets (and invest time learning ones which you already know)

Settings (UI) - in the background uses Azure's AI (when connected to the Internet)
- this mean that it will give it best to interpret your query and guess what you really want

# Settings:
- [How to integrate git-bash](https://dev.to/simbo1905/how-to-integrate-git-bash-with-visual-studio-code-on-windows-3217)

## List of Tweaks for VS Code (in Settings.json)
- Turn off the Minimap
- Move Sidebar Right
- Hide Open Editors
-
  - ❗ This list is temporary, the plan is to use `settings.json` as the documentation itself ❗
  - Sidebar on the right side - looks more intuitive
  - Trim white space … this is done for me on autosave so it is not necessary
  - `editor.tabSize` number of spaces when pressing `tab` key
  - `editor.formatOnSave`
  - `editor.formatOnPaste: true`
  - `editor.detectIndentation: false` - so it does not override editor.tabSize settings
  - ⭐ `files.exclude`	files/folders to exclude (ie, hide) in files explorer
      - you can use glob patterns
  - ⭐`emmet.includeLanguages`	- enable emmet abbreviations in languages which are not support by default
  - `javascript.updateImportsOnFileMove.enabled` - updates import statements when file name is changed for js files
  - `typescript.updateImportsOnFileMove.enabled`
  - `explorer.openEditors.visible: 0`	Toggle off "Open Editors" option in VS Code
  - `enable npm script explorer`	- to run npm scripts from VS Code (add play button)
  - in omnibox run "View: Toggle Minimap"

- Settings u VS code su takodje language specific (e.g., markdown, ts)
	- e.g, disable minmap only for markdown

`npm script explorer: true` - enable npm scripts in the file explorer sidebar

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

# Extensions
## Next To Consider
1. ⭐Plugins for Jest (to run tests from VS Code) - or to set configuration
2. ⭐[File Utils](https://marketplace.visualstudio.com/items?itemName=sleistner.vscode-fileutils)
   - you can [configure keyboard shortcuts](https://gist.github.com/elado/febe110a1df66089df1a2cddd0c801cb) in the File Explorer, like r to rename and d to duplicate.
3. [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
4. [Vue Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
5. [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
6. [Vim Mode Emulation](https://github.com/VSCodeVim/Vim)
   - [Neovim Extension]("https://github.com/asvetliakov/vscode-neovim") - should be BETTER alternative
7. [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) [colors different types of questions, TODOs, Questions…]
8. [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)
   - higlights hex codes and RGB values with their corresponding color
9.  [Auto Imports](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport) - like in IDEA
   - It looks like that Code is already doing this, but double check
10. [CSS Triggers](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.csstriggers) - Indicates cost of css properties (gives you a visual queues how expensive is a certain css property)
   - [article about CSS Performance](https://developers.google.com/web/fundamentals/performance/rendering)
   - https://csstriggers.com/ - here you can see how big impact has a different css property on browser (does it need to do a recomposition, a repainting, or rerendering)
11. [Markdown Lint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
12. ⬇ [Find Related Files](https://marketplace.visualstudio.com/items?itemName=eamodio.find-related)
    - can be used to find tests
13. ⬇ [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)
14. [Log File Highlighter](https://marketplace.visualstudio.com/items?itemName=emilast.LogFileHighlighter)
15. [CSS Peek](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek)
    - allows peeking to CSS ID and class definitions
16. [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)
17. [npm intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
18. [IntelliSense for CSS class names in HTML](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion)
19. [SQL Tools - DB Tools](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools) (support for many SQL DBs, MySQL, SQLite)
20. ⬇ [Version Lens](https://marketplace.visualstudio.com/items?itemName=pflannery.vscode-versionlens)
    - koristi *code lens* da ti pokaze koji su outdated paketi I slicno
21. ⬇ [Change Case](https://marketplace.visualstudio.com/items?itemName=wmaurer.change-case)
    - do I really need an extension for this?
22. ⬇⬇ [Expand Region](https://marketplace.visualstudio.com/items?itemName=letrieu.expand-region&ssr=false#review-details)
    - ("ctrl w" in IDEA; check if the extension works better than native feature)
23. [Power Mode](https://marketplace.visualstudio.com/items?itemName=hoovercj.vscode-power-mode) - it is cool for presentation puropses

## Installed
### Still Testing if Useful
1. [Markdown all in one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
2. Peacock
3. [Jest Snippets](https://marketplace.visualstudio.com/items?itemName=andys8.jest-snippets)
4. [JS ES6 Code Snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)
5. Gists
6. Paste Image
7. [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
8. [WakaTime](https://marketplace.visualstudio.com/items?itemName=WakaTime.vscode-wakatime) - Metrics on how much time you spend on different projects
9. [Code Time](https://marketplace.visualstudio.com/items?itemName=softwaredotcom.swdc-vscode) - measures how and where do you spend time coding
10. [TLDR](https://github.com/bmuskalla/vscode-tldr) - extension to show summarized help for many shell, Docker commands
11. [Project Manager](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager) - used to manage different Git projects in your VS code
12. [VS intellicode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
13. [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)


### Yes, please!
3. [Bracket Pair Colorizer 2](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2)
   - Previously [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
5. [Ident Rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow) - colorizes the indentation of your text alternating different colors on each step
6. remote-ssh - to connect VS Code to remote machine
7. [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
8. [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur) - Vue Tooling for VS Code
9. [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

## Decided Not To Use
1. [Quokka](https://marketplace.visualstudio.com/items?itemName=WallabyJs.quokka-vscode) - use CLI instead of this extension, e.g., `node filename.js`
2. [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode) - make screenshots of source codes
   - use web-based alternative: https://carbon.now.sh/
3. [Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - quite a big extensions, which I don't use that much
4. [Setting Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) - instead I am using native VS Code functionality
