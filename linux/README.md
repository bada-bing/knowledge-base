- [Useful Bash Commands](https://itnext.io/increase-developer-productivity-with-unix-bash-command-one-liners-2973bccd7600)
- http://www.bashoneliners.com/oneliners/popular/?source=post_page-----2973bccd7600----------------------
- https://quickleft.com/blog/command-line-tutorials-tips-tricks/
- ❓[splash](https://www.producthunt.com/posts/splash-cli) - change background
- https://itnext.io/increase-developer-productivity-with-unix-bash-command-one-liners-2973bccd7600

Sections
[Configuration](./configuration.md)
[CLI Tools](./cli.md)
[CLI - Additional Tools](./cli.cli.additional_tools.md)

General OS Tips:
- Increase mouse speed

# Important Questions
- Distinction between "home" and "root" dir
- [How to configure Linux](./configuration.md)
- [Most important CLI tools](./cli.md) [Files Management]
- [Other CLI tools](./additional_cli_tools.md)

# Useful Commands to consider
- tree (possibly needs to be installed)
	- gives the tree structure of the directory
- ping vs traceroute (traceroute gives the number and more details about hops to certain IP address)
- Command substitution:
  `` `command` or `$(command)` ``
- ``!! `` - run the last command
  - ``!!n `` - run the last command which starts with *n*
  - - ``sudo !! `` - run the last command with root user
- **TIP**: Generate a 100mb random file:
```dd if=/dev/urandom of=ridiculously_large_file.txt bs=1048576 count=100```

1. Restart System
   | Command | Linux | Windows (cmd/git-bash) |
   | ------------ | ------------ | -------: |
   | Restart| ```sudo reboot``` | ```shutdown //r``` |
   | | ```sudo init 6``` ||
   | | ```sudo shutdown -r now``` |  |
   | Shutdown|  | ```shutdown //s``` |
    - `//r` & `//s` is because we escape the first line or something like that

3. Shell Keyboard Shortcuts
   | Shortcut | Description |
   | ------------ | -------: |
   | CTRL + U | clears the input-line (prompt) |
   | CTRL + K | clears the input-line (from the cursor to the end of the prompt) |
   | CTRL + W | clears the last word/part/parameter (goes backwards) |
   | CTRL + L | clears the screen (i.e., clear) |
- When you are comfortable with these, check other commands in this [SO answer](https://askubuntu.com/questions/470966/shortcut-to-clear-command-line-terminal/471023#471023)

# Other
Standard Streams - stdin and stdout
- on the other hand there are File Descriptors - they represent unique numbers of currently open files (or something like that)

- POSIX - Portable OS Interface
	- This is used for System Level Integration and IO stuff
	- This is how Node.js knows how to print content to stdout (console)
- [Shell Special Parameters](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html#Special-Parameters)

- Globs
	- a sequence of literal and wildcard characters used to match filepath
	- [explaining globs](https://gulpjs.com/docs/en/getting-started/explaining-globs)
	-  Opposite of wildcard character is literal character
	- / - separator
	- \\ - escape character
		- 'glob_with_uncommon_\\*_character.js'
			§ an example: star is here escaped so it is actual literal charcter
	- Special Characters: ** (to include nested folders), ! (negative)

- General Linux Convention: "#" in cmd prompt that means that you are logged in as root

# Windows
- How to open always an app on the same monitor all the time
	Open the application, drag it to the screen you want it to open on, minimize it to half size (the middle square shape on the top far right - beside the X to close out the app or doc) and then close it out without maximizing it again.
	From now on it will open on that screen, until you change it by repeating this process on a different screen.
- print "path" variable in cmd: ```path```; in powershell: ```$env:path```
- How to run powershell script (ps1): [SO Link](https://stackoverflow.com/questions/2035193/how-to-run-a-powershell-script/2035209)
- [How to kill a service which is stuck at stopping](https://support.4it.com.au/article/how-to-kill-a-windows-service-which-is-stuck-at-stopping/)
  - find PID of service:  sc queryex servicename
  - shutdown service: taskkill /f /pid [PID]
- Copying to Clipboard
	in WSL you can do `clip.exe < ~/.ssh/some_file` or `cat ~/.ssh/some_file | clip.exe`
- UELI is like the omnibox is MacOS
