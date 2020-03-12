## Essentials
- watch - watch the output of a certain command every 2 seconds
- wget - retrieve **files** using HTTP, HTTPS, FTP, FTPS
  - ```wget <url>```
- ls, pwd
- echo - displays a line of text/string that is passed as an argument
- **touch** to create files (without content), **cat** to read files
  - touch can be used to modify timestamp of an (existing) file ("change when it is touched")
- cat - read/display the content of a file
  - can be used to copy files or to create new ones
  - ```cat somefile1 > somefile2```
  	- the right arrow is "output redirection operator"
	- redirect output of somefile1 to somefile2
	- ⭐[bat](https://github.com/sharkdp/bat) (cat with wings)
- awk
- tail
  - reads and outputs the last part of the file
  - useful for crashes (read only the stacktrace or something like that)
  - "tail -f ..." - automatically appends changes of the file to stdout
  	- it gives you live monitoring of some file (observe changes in the file in real time, e.g., log)
- mkdir - make directory
	- remove files "rm"; remove directories "rm -rf"
- mv & cp
- ln -s
	- make (sybmolic) links between files (makes symlinks)
	- Hardlink vs Symlink [difference - SO link](https://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link)
  	- Symbolic Links should NOT be used with relative paths!
  	- https://www.moreofless.co.uk/linux-difference-soft-symbolic-link-and-hard-link/
- find
  - find path -name filename
  	- e.g., find . -name index.js
  - find files of particular type
  	- find . -name "*.js"
		- [fzf](https://github.com/junegunn/fzf)
		- [fd](https://github.com/sharkdp/fd) - simple and fast alternative to find
			- check how to color the output



## Other Commands
- [jq](https://stedolan.github.io/jq/) - json query tool
  - like sed for JSON; it can colorize output and it has a lot of cool features
  - https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/

- killall
- nmap - port scanner
- pstree - show (active) processes in the form of a tree
- [uniq](https://en.wikipedia.org/wiki/Uniq) [used together with sort]
- history
- kill vs pkill
  - [Fkill-cli](https://github.com/sindresorhus/fkill-cli) - fabulously kill processes (fkill)
  - Tired of ps -ef | grep <process> and then kill <PID>? fkill kills processes by name, e.g. fkill node.
- fg
- pushd, popd, dirs
- service - access daemons running in the background
- [z](https://github.com/rupa/z) or alternative [autojump](https://github.com/wting/autojump)
  - jump to frequently vistied directory
