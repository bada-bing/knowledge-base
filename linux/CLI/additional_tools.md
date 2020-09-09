## Essentials
- cat, short for concatenate, is used to read, print, and combine files.
- echo displays a line of text either on standard output or to place in a file.
- sed is a popular stream editor often used to filter and perform substitutions on files and text data streams.
- awk is an interpreted programming language, typically used as a data extraction and reporting tool.
- sort is used to sort text files and output streams in either ascending or descending order.
- uniq eliminates duplicate entries in a text file.
- paste combines fields from different files. It can also extract and combine lines from multiple sources.
- join combines lines from two files based on a common field. It works only if files share a common field.
- split breaks up a large file into equal-sized segments.
- Regular expressions are text strings used for pattern matching. The pattern can be used to search for a specific location, such as the start - or end of a line or a word.
- grep searches text files and data streams for patterns and can be used with regular expressions.
- tr translates characters, copies standard input to standard output, and handles special characters.
- tee saves a copy of standard output to a file while still displaying at the terminal.
- wc (word count) displays the number of lines, words, and characters in a file or group of files.
- cut extracts columns from a file.
- less views files a page at a time and allows scrolling in both directions.
- head displays the first few lines of a file or data stream on standard output. By default, it displays 10 lines.
- tail displays the last few lines of a file or data stream on standard output. By default, it displays 10 lines.
- strings extracts printable character strings from binary files.
- The z command family is used to read and work with compressed files.

- watch - watch the output of a certain command every 2 seconds
# wget
wget is a command line utility that can capably handle the following types of downloads:

Large file downloads
Recursive downloads, where a web page refers to other web pages and all are downloaded at once
Password-required downloads
Multiple file downloads.
To download a web page, you can simply type wget <url>, and then you can read the downloaded page as a local file using a graphical or non-graphical browser.

# curl
Besides downloading, you may want to obtain information about a URL, such as the source code being used. curl can be used from the command line or a script to read such information. curl also allows you to save the contents of a web page to a file, as does wget.

You can read a URL using curl <URL>. For example, if you want to read http://www.linuxfoundation.org, type curl http://www.linuxfoundation.org.

To get the contents of a web page and store it to a file, type curl -o saved.html http://www.mysite.com. The contents of the main index file at the website will be saved in saved.html.

https://catonmat.net/cookbooks/curl

- wget - retrieve **files** using HTTP, HTTPS, FTP, FTPS
  - ```wget <url>```
- echo - displays a line of text/string that is passed as an argument
- **cat** read/display the content of a file
  - can be used to copy files or to create new ones
  - "output redirection operator": ```cat somefile1 > somefile2```
  	- redirect output of somefile1 to somefile2
	- ⭐[bat](https://github.com/sharkdp/bat) (cat with wings)
- awk


- `head, tail`
- if you want to print the first 5 lines from grub.cfg, use the following command: `$ head –n 5 grub.cfg`
tail is especially useful when you are troubleshooting any issue using log files, as you probably want to see the most recent lines of output.
Eg, to display the last 15 lines of somefile.log, use the following command: `$ tail -n 15 somefile.log`
To continually monitor new output in a growing log file: `$ tail -f somefile.log`
- This command will continuously display any new lines of output in atmtrans.log as soon as they appear. Thus, it enables you to monitor any current activity that is being reported and recorded.

- `tail` reads and outputs the last part of the file
  - useful for crashes (read only the stacktrace or something like that)
- `tail -f ...` - automatically appends changes of the file to stdout
  	- it gives you live monitoring of some file (observe changes in the file in real time, e.g., log)

- find
  - find path -name filename
  	- e.g., find . -name index.js
  	- `find . -maxdepth 3 -name '*ui.sh'`
  - find files of particular type
  	- find . -name "*.js"
		- [fzf](https://github.com/junegunn/fzf)
		- [fd](https://github.com/sharkdp/fd) - simple and fast alternative to find
			- check how to color the output
			- [fd vs find](https://search.app.goo.gl/GQ2Nsqx)

## Other Commands
- [jq](https://stedolan.github.io/jq/) - json query tool
  - like sed for JSON; it can colorize output and it has a lot of cool features
  - https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/

- killall
- nmap - port scanner
  - https://www.techrepublic.com/article/how-to-listen-to-port-traffic-on-a-linux-server/
- pstree - show (active) processes in the form of a tree
- [uniq](https://en.wikipedia.org/wiki/Uniq) [used together with sort]
- history
- kill vs pkill
  - [Fkill-cli](https://github.com/sindresorhus/fkill-cli) - fabulously kill processes (fkill)
  - Tired of ps -ef | grep <process> and then kill <PID>? fkill kills processes by name, e.g. fkill node.
- fg
- Directory History: `pushd`, `popd`, `dirs`
  - https://www.howtogeek.com/659146/how-to-use-pushd-and-popd-on-linux/
- `service` - access daemons running in the background
- [z](https://github.com/rupa/z) or alternative [autojump](https://github.com/wting/autojump)
  - jump to frequently vistied directory
- tree (possibly needs to be installed)
	- gives the tree structure of the directory
	- `tree -d` gives only directories (only files)
- ping vs traceroute (traceroute gives the number and more details about hops to certain IP address)

netstat
- https://www.howtogeek.com/513003/how-to-use-netstat-on-linux/

lsof
- https://www.ubuntupit.com/simple-and-effective-lsof-command-in-linux/

this is some kind of documentation tools - https://github.com/rsyi/metaframe
- mostly for searching and finding tables

notify-send: https://www.thegeekstuff.com/2010/12/ubuntu-notify-send/


check `at` & `locate` commands
