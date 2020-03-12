1. Pre-requisites & Aesthetics
  - Install [Fira Code](https://github.com/tonsky/FiraCode/wiki/Linux-instructions#installing-with-a-package-manager)
  - [Optional] [Background Wallpapers](https://wallpaperhub.app/wallpapers)

- Consider Fish (https://fishshell.com/) with Starship configuration [https://starship.rs/config/#git-status](https://starship.rs/config/#git-status)

2. Switch to ZSH | (or Fish)

- Reasons:
  - Easier Prompt Definitions. Particularlly, dynamic/multiline prompts
  - Smart & Fast Autocompletions (case-insensitive, smart defaults)
  - Path Expansion (e.g., `cd /v/w [TAB]` => `cd /var/www`)
  - ❔ Spelling Correction (check **setopt correct**)
  - Keybindings (google how to do it)
- Configure your Shell & Extensions:
  - Star from this article on how to optimize your terminal&shell [article](https://www.freecodecamp.org/news/coding-like-a-hacker-in-the-terminal-79e22954968e/)
  - oh-my-zsh - Large Community-Driven Framework for all sorts of bells and whistles
  - Powerline
    - What is difference between Powerline and oh-my-zsh
    - Different Powerline configurations: [Powerline9k:Show-Off-Your-Config](https://github.com/Powerlevel9k/powerlevel9k/wiki/Show-Off-Your-Config)
    - _Powerline10k_
    - Configure your Shell
    - https://github.com/alebcay/awesome-shell
    - https://github.com/denysdovhan/spaceship-prompt
  - [.dotfiles](https://github.com/mkjmdski/.dotfiles) - includes optimized setup for some essential tools (vim, vscode, zsh) - read the article (link in github repo)
- Other:
  - ❔ The zsh line editor
  - Command History in zsh [~/zsh_history] (check if it has ".", i.e., /.zsh_history)

3. Tmux and Tmuxp

- Tmuxp is the wrapper (written in Python) around Tmux which makes easier to configure Tmux sessions
- It can be used to automatise steps, when there are multiple shells (and commands) which you need to execute often (e.g, to start local development)
