# Important Questions
- Distinction between "home" and "root" dir
- [How to configure Linux](./configuration.md)
- [Most important CLI tools](./cli.md) [Files Management]
- [Other CLI tools](./additional_cli_tools.md)

# Useful Commands to consider
- ⭐❗❗❗Shortcuts: https://pop.system76.com/docs/keyboard-shortcuts/
- Command substitution:
  `` `command` or `$(command)` ``
- ``!! `` - run the last command
  - ``!!n `` - run the last command which starts with *n*
  - - ``sudo !! `` - run the last command with root user
- **TIP**: Generate a 100mb random file:
```dd if=/dev/urandom of=ridiculously_large_file.txt bs=1048576 count=100```
- which vs whereis (looks in a broader range of system directories)
- https://www.networkworld.com/article/3453032/cleaning-up-with-apt-get.html

1. Restart System
   | Command  | Linux                      | Windows (cmd/git-bash) |
   | -------- | -------------------------- | ---------------------: |
   | Restart  | ```sudo reboot```          |     ```shutdown //r``` |
   |          | ```sudo init 6```          |                        |
   |          | ```sudo shutdown -r now``` |                        |
   | Shutdown |                            |     ```shutdown //s``` |
    - `//r` & `//s` is because we escape the first line or something like that

  - Restart Graphical Desktop
    - Stop it: sudo systemctl stop gdm (or sudo telinit 3)
    - Restart it: sudo systemctl start gdm (or sudo telinit 5)



## Cool Tips
	2. "fc" - to fix a really long command which you messed up (opens the editor)
	3. Create a super fast ram disk (this is temporary but it looks really cool)
		- mkdir -p /mnt/ram
		- mount -t tmpfs tmpfs /mnt/ram -o size=8192M
	4. If you add the space in front of the command the command will not be added to the history
		- " ls -l"
	5. tunnel with ssh (local port 3337 -> remote host's 127.0.0.1 on port 6379)
		- ssh -L 3337:127.0.0.1:6379 root@emkc.org -N
	6. Quckly create folders
		- mkdir -p folder/{sub1,sub2}/{sub1,sub2,sub3}
	7. Exit terminal but leave all the (sub)processes running
		- disown -a && exit

# Other
Standard Streams - stdin and stdout
- on the other hand there are File Descriptors - they represent unique numbers of currently open files (or something like that)

- POSIX - Portable OS Interface
	- This is used for System Level Integration and IO stuff
	- This is how Node.js knows how to print content to stdout (console)
- [Shell Special Parameters](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html#Special-Parameters)

- General Linux Convention: "#" in cmd prompt that means that you are logged in as root

Also worth knowing is the use of '!$' - ie:
- `mkdir -p /path/to/new/dir`
- `cd !$`
- to go to previous directory, run `cd -`
Will take you to the new dir. '!$' just means 'last argument in the last command'. Very useful and will save you bulk time.

Shortcuts In File Manager:
  | Shortcut          |                             Description |
  | ----------------- | --------------------------------------: |
  | CTRL-H            |                       show hidden files |
  | CTRL-1 / CTRL - 2 | - Switch between Icons and List formats |
  | CTRL-L            |   Location Bar in File Manager/ Browser |
