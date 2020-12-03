## Essentials
- `cat` short for concatenate, is used to read, print, and combine files.
- `echo` displays a line of text either on standard output or to place in a file. displays a line of text/string that is passed as an argument
- `sed` is a popular stream editor often used to filter and perform substitutions on files and text data streams.
- `awk` is an interpreted programming language, typically used as a data extraction and reporting tool.
- `sort` is used to sort text files and output streams in either ascending or descending order.
- `uniq` eliminates duplicate entries in a text file.
- `paste` combines fields from different files. It can also extract and combine lines from multiple sources.
- `join` combines lines from two files based on a common field. It works only if files share a common field.
- `split` breaks up a large file into equal-sized segments.
- `tr` translates characters, copies standard input to standard output, and handles special characters.
- `tee` saves a copy of standard output to a file while still displaying at the terminal.
- `wc` (word count) displays the number of lines, words, and characters in a file or group of files.
- `cut` extracts columns from a file.
- `less` views files a page at a time and allows scrolling in both directions.
- `head` displays the first few lines of a file or data stream on standard output. By default, it displays 10 lines.
- `tail` displays the last few lines of a file or data stream on standard output. By default, it displays 10 lines.
- `strings` extracts printable character strings from binary files.
- `z` command family is used to read and work with compressed files.
- `watch` - watch the output of a certain command every 2 seconds

## Other Commands
- [jq](https://stedolan.github.io/jq/) - json query tool
  - like sed for JSON; it can colorize output and it has a lot of cool features
  - https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/

- killall
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

lsof
- https://www.ubuntupit.com/simple-and-effective-lsof-command-in-linux/

notify-send: https://www.thegeekstuff.com/2010/12/ubuntu-notify-send/

check `at` & `locate` commands
