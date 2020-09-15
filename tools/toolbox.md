- organize this chapter according to this list, if becomes too big, make more chapters out of it
- this list is too big, organize it into chapters (eg, Development, Management Tools, ...)
# Toolbox
1.  OmniLauncher
    1.  UELI (Windows)
    2.  Ulauncher (Linux)
2.  Password Manager
    1.  KeePass (Windows)
        1.  consider migrating to KeePassXC on Windows as well ❗
    2.  KeePassXC (Linux)
3. Editors
   1. [VS Code](./code/README.md)
   2. [VIM](./vim.md)
   3. IDE: IntelliJ IDEA ❓
4. [Browsers](./browsers.md)
   1. Chrome       - Work-Related
   2. Brave        - Personal
   3. Firefox      - Personal
   * I will start testing MS Edge Soon as a potential Replacement for either Brave or Chrome
5. Mail Client
   1. Outlook      - Work-Related (Windows)
   2. Thunderbird  - Personal (Linux)
6. Calendar Client
   1. MineTime     -
7. Snippet Manager
   1. Cacher
8. Bookmarks Manager
   1. Raindrop IO
   2. Toby
9. Notebook Manager
   1. OneNote
10. Shell: ZSH + Starship Prompt + oh-my-zsh
    0. no `fish` until I am sure what I am doing (since fish is not POSIX compliant)
    1. git-bash - Windows ❓ (do I need it)
    2. `oh-my-zsh` configuration manager
       - Large Community-Driven Framework for all sorts of bells and whistles
    - Use `zc` command/alias to edit `.zshrc` file
11. Terminal Emulator:
   2. WSL 1 & 2 in Windows ⭐ + Windows Terminal
   3. Konsole in Linux
   4. 3. Tmux and Tmuxp
    - `Tmuxp` is a Tmux wrapper (written in Python) which simplifies configuration of Tmux sessions
    - Used to automatise steps, when there are multiple shells (and commands) which you execute often (e.g, to start local development)
12. Encryption
   5. VeraCrypt
   6. Cryptomator
13. Docker
14. VPN
    1.  ExpressVPN
15. Space-Repetition Learning Software
    1.  ANKI
16. VCS
    1.  Git

17. Organization Tools
  1. Zenkit Kanban
  2. Todo - MS Todo

18. Windows Specific
    1.  PowerToys


What about web-tools (e.g, pocket)

# Configuration

- Important plugins: zsh-autosuggestions & zsh-syntax-highlighting
```
- Next you need to enable plugins which you want to use in your zshrc
  - `$ZSH_CUSTOM` - the path to custom_plugins

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
plugins+=(zsh-nvm) # update this line to ~/.zshrc
# ! zsh-auto-suggestions are missing in this installation section of plugins
```

# Windows Configuration
- Consider saving following settings files in dotfiles instead of Gists (once you publish the project to the GitHub)
1. WT `settings.json` - stored in `Windows` Gist
   - ❌ Gist is not the most managable solution since I need to manually copy the content of settings and pics are missing
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


# General OS Tips: (X-Platform Tips)
- Increase mouse speed

## Windows OS Settings
   - this is really useful... collect some ideas and how and where to collect them
