To sync settings I use the plugin *Setting Sync*
- connect the extension to github (to access gist with settings)
- these settings are based on the lectures and tips and best practices which I encountered.
- [consider to switch some instructions what to do to gist]
  - [separate what is clear instruction and what is information and extract instructions to gist]

What to consider when customizing VS Code:
	- Theme
		- Current Theme: One Dark Pro [alternative: [Dracula](https://marketplace.visualstudio.com/items?itemName=dracula-theme.theme-dracula)]
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

Some settings:
  - My sidebar is on the right side… and it looks much more intuitive once you are used to
  - Trim white space … this is done for me on autosave so it is not necessary
  - editor.tabSize	number of spaces when pressing tab key
  editor.formatOnSave
  "editor.formatOnPaste": true
  editor.detectIndentation	set to false, so it does not override editor.tabSize settings
  ⭐ files.exclude	files or folders to exclude in files explorer
    - you can use glob patterns
    - true indicates to hide folders
  ⭐emmet.includeLanguages	- enable emmet abbreviations in languages which are not support by default
  javascript.updateImportsOnFileMove.enabled - updates import statements when file name is changed for js files
  typescript.updateImportsOnFileMove.enabled
  "explorer.openEditors.visible": 0	Toggle off "Open Editors" option in VS Code
  enable npm script explorer	- to run npm scripts from VS Code (add play button)
  - in omnibox run "View: Toggle Minimap"

- Settings u VS code su takodje language specific (e.g., markdown, ts)
	- e.g, disable minmap only for markdown

# Extensions
## Next To Consider
1. [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
2. [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
3. ⭐[File Utils](https://marketplace.visualstudio.com/items?itemName=sleistner.vscode-fileutils)
   - you can [configure keyboard shortcuts](https://gist.github.com/elado/febe110a1df66089df1a2cddd0c801cb) in the File Explorer, like r to rename and d to duplicate.
4. [Vue Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
5. [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) [colors different types of questions, TODOs, Questions…]
6. [Auto Imports](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport) - like in IDEA
   - It looks like that Code is already doing this, but double check
7. ⬇ [Find Related Files](https://marketplace.visualstudio.com/items?itemName=eamodio.find-related)
8. ⬇ [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)
9. ⬇ [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)

## Installed
### Still Testing if Useful
1. [Markdown all in one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
2. Peacock
3. [Jest Snippets](https://marketplace.visualstudio.com/items?itemName=andys8.jest-snippets)
4. [JS ES6 Code Snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)
5. Gists
6. Paste Image

### Yes, please!
3. [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
4. remote-ssh - to connect VS Code to remote machine
6. [Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
7. [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
8. [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur) - Vue Tooling for VS Code
9. [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)


## Decided Not To Use
1. [Quokka](https://marketplace.visualstudio.com/items?itemName=WallabyJs.quokka-vscode) - use CLI instead of this extension, e.g., `node filename.js`
2. [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode) - make screenshots of source codes
   - use web-based alternative: https://carbon.now.sh/
