# Read Contents of Text Files
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
