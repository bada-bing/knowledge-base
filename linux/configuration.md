--- THIS PAGE DOES NOT BELONG HERE ---

## Shell - ZSH + Starship Prompt
  - `oh-my-zsh` configuration manager
   - NOT fish, at least until I am sure what I am doing.

```bash
sudo apt install zsh
# Make it a default shell
chsh -s $(which zsh)
# Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# install starship
curl -fsSL https://starship.rs/install.sh | bash
eval "$(starship init zsh)" # Add this line to ~/.zshrc
```
- Next you need to enable plugins which you want to use in your zshrc
  - `$ZSH_CUSTOM` - the path to custom_plugins

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
plugins+=(zsh-nvm) # update this line to ~/.zshrc
```
- Important plugins: zsh-autosuggestions & zsh-syntax-highlighting
  1. [ZSH Documentation](http://zsh.sourceforge.net/Doc/Release/zsh_toc.html)
   2. add these lines to ~/.zshrc:
        ```
        export EDITOR="code" # your favorite editor goes here
        alias zc="$EDITOR ~/.zshrc"
        ```


1. Pre-requisites & Aesthetics
  - Install [Fira Code](https://github.com/tonsky/FiraCode/wiki/Linux-instructions#installing-with-a-package-manager)
  - [Optional] [Background Wallpapers](https://wallpaperhub.app/wallpapers)
- Reasons:
  - Smart & Fast Autocompletions (case-insensitive, smart defaults)
  - Path Expansion (e.g., `cd /v/w [TAB]` => `cd /var/www`)
  - ❔ Spelling Correction (check **setopt correct**)
  - Keybindings (google how to do it)
- Configure your Shell & Extensions:
  - oh-my-zsh - Large Community-Driven Framework for all sorts of bells and whistles
  - Powerline
    - What is difference between Powerline and oh-my-zsh
    - Different Powerline configurations: [Powerline9k:Show-Off-Your-Config](https://github.com/Powerlevel9k/powerlevel9k/wiki/Show-Off-Your-Config)
    - _Powerline10k_
    - Configure your Shell
    - https://github.com/alebcay/awesome-shell

- Other:
  - ❔ The zsh line editor
  - Command History in zsh [~/zsh_history] (check if it has ".", i.e., /.zsh_history)


3. Tmux and Tmuxp

- Tmuxp is the wrapper (written in Python) around Tmux which makes easier to configure Tmux sessions
- It can be used to automatise steps, when there are multiple shells (and commands) which you need to execute often (e.g, to start local development)

# Windows Configuration
- Consider saving these settings files in dotfiles instead of Gists (once you publish the project to the GitHub)
1. WT `settings.json` - stored in `Windows` Gist
   - ❌ not the most managable solution since I need to manually copy the content of settings and pics are missing
   - is it possible to split settings file somehow ❓
   - you will need to install Cascadia Code PL (https://github.com/microsoft/cascadia-code/releases)
   - website for different themes https://atomcorp.github.io/themes/
2. Ueli Settings ❌
   - Settings are stored in the `Windows` Gist.
   - Once you install the application, import them using the provided option in the settings of the app.
   - ⭐ Important, it is improtant to have the directory structure consistent across all machines, since some shortcuts will not work otherwise
3. Power Toys
   - The most important settings which are customized in the same Gist as WT Settings
   - This is the set of instructions to me what I should change, the tool does NOT have extractable settings...

## Other Applications
4. Docker for Desktop
   - currently the only important setting is to use WSL2 as the engine

## Windows OS Settings
   - this is really useful... collect some ideas and how and where to collect them
