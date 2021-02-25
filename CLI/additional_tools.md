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
- `history`
- [jq](https://stedolan.github.io/jq/) - json query tool
  - like sed for JSON; it can colorize output and it has a lot of cool features
  - https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/
- `read` is used to read the input
  - e.g., `read LINE`
	- you enter some text and that is stored in ENV called LINE
- `file`
	- used to determine the type of the file (or directory)
- `sort`
	- used to sort lines in data file
- [uniq](https://en.wikipedia.org/wiki/Uniq) [used together with sort]
- `lsof`
  - https://www.ubuntupit.com/simple-and-effective-lsof-command-in-linux/
- `notify-send`: https://www.thegeekstuff.com/2010/12/ubuntu-notify-send/
- [z](https://github.com/rupa/z) or alternative [autojump](https://github.com/wting/autojump)
  - jump to frequently vistied directory
  - How to install:
    ```bash
    # Download to latest to home dir
    wget https://raw.githubusercontent.com/rupa/z/master/z.sh -O ~/z.sh
    # Add to .bashrc
    echo . /path/to/z.sh >> ~/.bashrc
    # Add to .zshrc
    echo . /path/to/z.sh >> ~/.zshrc
    ```
- `reset` - resets the shell and fixes usually all weird problems
- check `tail -f` useful for logging
- `watch` command --- watches for file changes

**flags** are sometimes called **switch**

alternative to `calendar` is `ncal -e` (determines when the easter it is)

`curl http://wttr.in/paderborn`
	- gives the current weather
	- create alias for that
