Common VS Code and IntelliJ Settings:
Theme: One Dark Pro
Font: Fira Code
Font Size: 15
Atom Material Icons
Synchronize settings in VS Code and IntelliJ: [Editorconfig File](https://editorconfig.org/)

My Workflow is currently based on:
1. Idea IntelliJ
2. [VS Code](./code)
3. Fish as Shell/Konsole as Terminal Emulator
    - POSIX Compliant Alternative to Fish: ZSH
      - Important plugins: zsh-autosuggestions & zsh-syntax-highlighting
      1. [ZSH Documentation](http://zsh.sourceforge.net/Doc/Release/zsh_toc.html)
      2. Important Plugins
      3. add these lines to ~/.zshrc:
          ```
          export EDITOR="code" # your favorite editor goes here
          alias zc="$EDITOR ~/.zshrc"
          ```

4. [VIM](./vim.md)
5. [Browsers](./browsers.md)

It can happen that this chapter gets into the conflict with [tools](./../linux/README.md) chapter, but you don't need to be concerned about that for now.

Additonal Tools
- [Windows Terminal](#windows-terminal)
### Windows Terminal
- git-bash


Future Improvements:
	- Reconfigure capsLock
	- [Vimium](https://github.com/philc/vimium/blob/master/README.md)
		- potential to increase productivity is great, but it requires time to be understood and learned
  -
