🌟🌟https://dotfiles.github.io/

The Project URL: https://github.com/bada-bing/dotfiles

# Rationale
- [anishathalye/managing-your-dotfiles/](https://www.anishathalye.com/2014/08/03/managing-your-dotfiles/)
1. All dotfiles in one directory (supported with VCS)
2. Symbolic linking of dotfiles (to home directory)
3. Git Submodules for managing plugins/add-ons
  - Eg, to add submodule: `git submodule add https://github.com/anishathalye/dotbot dotbot`
  - Eg, to update submodule: `git submodule update --init --recursive`
  - Eg, to update to latest version : `git submodule update --init --remote`

# Decision
- Workflow:
  - Migrate on the fly, as you need something. Similar to the approache used for KeePass Passwords.
  - Not necessary to have a migrating phase and to overcomplicate it.

- Will use [Dotbot](https://github.com/anishathalye/dotbot) tool for managing dotfiles
  a. No dependencies
  b. YAML-based syntax configuration
  c. Makes easier managing of files which not necessarily go to `~/` as well (eg, `.config/`)
  d. Makes easier managing of plugins (git submodules)

# Which Tools
- all CLI tools which have custom configuration - [Toolbox](./toolbox.md)

# Open Question
1. What about Windows Files
- It looks that MS as well have symbolic links... use that for these files
- additionally, Dotbot have some base and local configurations... means you can extend something for a specific machine... that way you can add configuration to Windows

# Installation
0. `cd ~; git clone git@github.com:bada-bing/dotfiles.git` clone it in the subdirectory in home folder
1. `./install` run it

- ❗ REQUIRED: only the first time when setting up the project ❗
# How to setup the Project
0. Init git repository `git init`
1. Install dotbot as Git submodule (ssh link)
   1. `git submodule add git@github.com:anishathalye/dotbot.git`
   2. `git config -f .gitmodules submodule.dotbot.ignore dirty` # ignore dirty commits in the submodule
2. `cp dotbot/tools/git-submodule/install .` Copy the install.sh script from the dotbot submodule
3. `touch install.conf.yaml` set up configuration file
