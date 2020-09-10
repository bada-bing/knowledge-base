- https://www.anishathalye.com/2014/08/03/managing-your-dotfiles/

# Rationale
1. All dotfiles in one directory (which is version-controlled)
2. Symbolic linking of dotfiles (to home directory)
3. Git Submodules for managing plugins/add-ons
  - Eg, to add submodule: `git submodule add https://github.com/anishathalye/dotbot dotbot`
  - Eg, to update submodule: `git submodule update --init --recursive`
  - Eg, to update to latest version : `git submodule update --init --remote`

# Decision
- Will use [Dotbot](https://github.com/anishathalye/dotbot) tool for managing dotfiles
  a. No dependencies
  b. YAML-based syntax configuration
  c. Makes easier managing of files which not necessarily go to `~/` as well (eg, `.config/`)
  d. Makes easier managing of plugins (git submodules)

# Workflow
1. Create dotfiles directory ✔
2. Make a list of dotfiles of interest "Which Tools" ✔
3. Migrate your first dotfile (.zshrc) ✔
4. Migrate your first plugins (for zsh)
5. Publish to github

# Which Tools
1. ZSH + Starship + oh-my-zsh - [configuration page](./configuration.md)
1. Vim ❓
2. Tmux ❓

# Open Question
1. What about Windows Files
- It looks that MS as well have symbolic links... use that for these files
- additionally, Dotbot have some base and local configurations... means you can extend something for a specific machine... that way you can add configuration to Windows
