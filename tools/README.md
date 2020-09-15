-  [Toolbox](./toolbox.md)
-  [dotfiles](dotfiles.md) as a solution to manage CLI settings and customizations
-  [CLI tools](./CLI/README.md)
   -  [Vim](./CLI/vim.md) subsection as well belong here
-  [VS Code](./code/README.md)
-  [Browsers](./browsers/README.md)
-  [IDE - IntelliJ Idea](./idea.md)

Similar to the approach in [VS Code](./code/README.md) section, define your expectations and requirements
- (general guideline) aim to install only what is really necessary! Use as much as possible VMs and Docker Containers

# Configuration
Goes hand in hand with installation instructions even though it is not the same thing
## The Process
1. What and how should be synchronized?
- I will aim to synchronize settings for each tool which is customized (even if 1 line is customized)
  - if extracting, storing and importing/referencing settings is not an option, I will document instructions on what and how to update in order to use the tool in a way I am used to (e.g, PowerToys)
- everything which is possible should be automatized
- **settings** should be kept at a single location (so they are easy to reach and check)
  - here I mean the snapshot of the optimal working settings for the each tool (or the instructions how to setup tool, if export of settings is not possible)
- settings should be stored on the cloud
  - Preferably in `dotfiles` project (or alternatively Github Gists)
  - should I backup the `settings`?
    - Yes, this can be easily attached to backup process (once you define it), together with backup of other data.
- Files which settings depend on should also be saved together with settings (eg, a picture for the background of a terminal emulator)
- In a similar way Instructions which need to be executed as a prerequisite should be properly documented (e.g, `install fira code font`)
  - aim as much as possible to pack into the dotfiles
    - once again, there are `local` version of `install.config.yaml` and aim to use that (e.g, to automatically install font before linking zshrc file)
- everything will be documented!

- All Programming Related stuff wil go into dotfiles
- Tools which enable the profiles which can save the settings will be utilized and that will be as well documented
  - browsers and vs code
    - do I want to use the same email account for these profiles?
    - what about brave?
1. What about MineTime/Thunderdird? (and other stuff for which I don't have settings right now)
2. What about plugins for KeePass for example?
   1. this will be documented

- ❗❗❗ As you update the installation instructions, update also the approach how to share/store/document customizations of these tools
- in other words, update as you need it! ❗❗❗

- Create .editorconfig template file with these settings
## Common VS Code and IntelliJ Settings:
- Theme: One Dark Pro
- Font: Fira Code
- Font Size: 15
- Atom Material Icons
- LF End-of-Line (EOL)
Synchronize settings in VS Code and IntelliJ: [Editorconfig File](https://editorconfig.org/)
- an Idea, create your own editorconfig file which you will place here (you can include settings like `theme` and `font` in comments, if they are not recognized by the editorconfig tool)

- When synchronizing VS Code, you will have to provide some API keys or similar info (which is not synchronized by default)
  - this data will be stored in KeePass and here I will store instructions
  - 1. you need Wakatime APi Key, that is stored in KeePass from now on


Define Requirements (Windows Terminal)
	- eg, each shell should be unique
		- transparent background and color tab
