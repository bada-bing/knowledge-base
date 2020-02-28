The section about linux
- material from both the book about linux and bash scripting and from the edX course "Introduction to Linux"

# Important Questions
- Distinction between "home" and "root" dir
- [How to configure Linux](./configuration.md)
- [Most important CLI tools](./cli.md)

# Useful Commands to consider
- tree (possibly needs to be installed)
	- gives the tree structure of the directory
- ping vs traceroute (traceroute gives the number and more details about hops to certain IP address)
- kill vs pkill
- Command substitution:
  `` `command` or `$(command)` ``
- ``!! `` - run the last command
  - ``!!n `` - run the last command which starts with *n*
  - - ``sudo !! `` - run the last command with root user

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


# Windows
- How to open always an app on the same monitor all the time
	Open the application, drag it to the screen you want it to open on, minimize it to half size (the middle square shape on the top far right - beside the X to close out the app or doc) and then close it out without maximizing it again.
	From now on it will open on that screen, until you change it by repeating this process on a different screen.
- print "path" variable in cmd: ```path```; in powershell: ```$env:path```
- How to run powershell script (ps1): [SO Link](https://stackoverflow.com/questions/2035193/how-to-run-a-powershell-script/2035209)
