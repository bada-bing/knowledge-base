# File Descriptors
When commands are executed, by default there are three standard file streams (or descriptors) always open for use: standard input (standard in or stdin), standard output (standard out or stdout) and standard error (or stderr).

File Descriptors, ie, Standard File Streams
- `stdin` (value/file-descriptor-code: `0`, e.g., keyboard)
- `stdout` (value/file-descriptor-code: `1`, e.g., terminal)
- `stderr` (value/file-descriptor-code: `2`, e.g., log file)

In Linux all open files are represented internally by what are called **file descriptors**.
Simply put, these are represented by numbers starting at zero.
`stdin` is file descriptor `0`, `stdout` is file descriptor `1`, and `stderr` is file descriptor `2`.
Typically, if other files are opened in addition to these three, which are opened by default, they will start at file descriptor 3 and increase from there.
- that means that also stdin/stderr/stoud are streams which are considered as open files

# Package Management system - Install Software & Packages
- 2 levels of package managers
  - dpkg - debian package manager (default low level package manager for debian and ubuntu)
  - apt - advanced package tool is higher-level package management system
- a low-level tool (such as **deb** or rpm)
  - a low-level tool (such as dpkg or rpm) takes care of the details of unpacking individual packages, running scripts, getting the software installed correctly
    - `dpkg --list | less (list all packages)`
    - `dpkg --listfiles bzip2 (show files of the package)`
- **apt** (high-level pacakge manager)
    - `sudo apt-cache search wget2`
  - while a high-level tool (such as apt-get, yum, dnf or zypper) works with groups of packages, downloads packages from the vendor, and figures out dependencies.

[diff between apt update and apt upgrade](https://www.youtube.com/watch?v=tNT9Hm8fpOA)

Most of the time users need to work only with the high-level tool, which will take care of calling the low-level tool as needed. Dependency resolution is a particularly important feature of the high-level tool, as it handles the details of finding and installing each dependency for you. Be careful, however, as installing a single package could result in many dozens or even hundreds of dependent packages being installed.

which vs whereis commands

`info make`
- utility to give information for apps in the system..
- ❓difference to man
- use n and p to scroll (n as next)
- http://www.differencebetween.net/technology/software-technology/difference-between-man-and-info/

# User Environment
`who -a` - currently logged in users
`whoami` - current user

The command shell program uses one or more **startup files** to **configure the user environment**.
- Files in the `/etc` directory define global settings for all users, while initialization files in the user's `home` directory can include and/or override the global settings.
- The startup files can do anything the user would like to do in every instance of the command shell, such as:
* Customizing the prompt
* Defining command line shortcuts and aliases
* Setting the default text editor
* Setting the path for where to find executable programs.

## Order of Startup Files
The standard prescription is that when you first login to Linux, `/etc/profile` is read and evaluated, after which the following files are searched (if they exist) in the listed order:
* `~/.bash_profile`
* `~/.bash_login`
* `~/.profile`
`~/.` denotes the user's home directory

The `Linux login shell` evaluates whatever startup file that it comes across first and ignores the rest. This means that if it finds ~/.bash_profile, it ignores ~/.bash_login and ~/.profile. Different distributions may use different startup files.

However, every time you create a new shell, or terminal window, etc., you do not perform a full system login; only a file named `~/.bashrc` file is read and evaluated.
Although this file is not read and evaluated along with the login shell, most distributions and/or users include the `~/.bashrc` file from within one of the three user-owned startup files.

Most commonly, users only fiddle with `~/.bashrc`, as it is invoked every time a new command line shell initiates, or another program is launched from a terminal window, while the other files are read and executed only when the user first logs onto the system.

Recent distributions sometimes do not even have .bash_profile or .bash_login (Ubuntu) and some just have it do little more than `include .bashrc`.

![Order of the Startup Files](assets/2020-03-27-08-19-12.png)

## Aliases
You can create customized commands or modify the behavior of already existing ones by creating aliases.
Most often, these aliases are placed in your `~/.bashrc` file so they are available to any command shells you create.
- `alias cmd1="echo $?"`
  - NO spaces around the equal sign and the alias definition needs to be placed within either single or double quotes if it contains any spaces.
- `alias` with no arguments will list currently defined aliases.
- `unalias` removes an alias.

# Creating Temporary Files and Directories

Temporary files (and directories) are meant to store data for a short time.
These files should disappear when the program using them terminates.
`touch` is not the best option to create a temporary file, since it can make it easy for hackers to gain access to your data.
This is particularly true if the name and the file location of the temporary file are predictable.

The best practice is to create **random and unpredictable filenames** for temporary storage.
One way to do this is with the `mktemp` utility, as in the following examples.

Command	Usage
- The XXXXXXXX is replaced by the mktemp utility with random characters to ensure the name of the temporary file cannot be easily predicted and is only known within your program.
- Create a temporary file: `TEMP=$(mktemp /tmp/tempfile.XXXXXXXX)`
- Create a temporary directory: `TEMPDIR=$(mktemp -d /tmp/tempdir.XXXXXXXX)`

# Discarding Output with /dev/null
Certain commands (like find) will produce voluminous amounts of output, which can overwhelm the console. To avoid this, we can redirect the large output to a special file (a device node) called /dev/null. This pseudofile is also called the bit bucket or black hole.

All data written to it is discarded and write operations never return a failure condition. Using the proper redirection operators, it can make the output disappear from commands that would normally generate output to stdout and/or stderr:

random numbers can be generated by using the $RANDOM environment variable

The default display manager for GNOME is gdm
- presents user with the login screen
- Logging out through the desktop env kills all the processes in your current X session and returns to the display manager login screen
Suspending puts the computer in sleep mode

Network Time Protocol NTP - protocol for setting the locale time via Internet Servers

`xdpyinfo` gives basic info about display
- e.g., `xdypinfo | grep dim` - print the resolution

Absolute path starts with "/"

tree - list files&dirs in tree shape
tree - d : only show directories

[Missing Semester - Cambridge, 2020](https://www.youtube.com/playlist?list=PLyzOVJj3bHQuloKGG59rS43e29ro7I57J)

xargs takes the lines of input and turns them into arguments

# MISC
In most UNIX systems logs are usually stored in `/var/log`
- eg, `/var/log/system.log` a lot of info about OS
- `/var/log/system.log | lnav` check this tool for reading logs
- another tool is `log show --last 10s`
`logger` command can be used to print log statements into log files
`strace` is the tool which will help you to check what of system calls are made when executing some application or some script
- system calls are the calls made to OS (which OS needs to do/delgate) like network calls, reading a file, ...
- `strace -e lstat ls -l` lstat flag lists the properties of files ... something like that

you can integrate vim with some linting tools... so that you see the errors in the same way you see them in the vscode.

- Printing: CUPS
- PDF Manipulation: `qpdf`  is widely available on Linux distributions and is very full-featured.
- encrypt pdfs: `pdftk`
The CUPS interface is available at http://localhost:631.
lp and lpr are used to submit a document to CUPS directly from the command line.
lpoptions can be used to set printer options and defaults.
PostScript effectively manages scaling of fonts and vector graphics to provide quality prints.
enscript is used to convert a text file to PostScript and other formats.
Portable Document Format (PDF) is the standard format used to exchange documents while ensuring a certain level of consistency in the way the documents are viewed.
pdftk joins and splits PDFs; pulls single pages from a file; encrypts and decrypts PDF files; adds, updates, and exports a PDF’s metadata; exports bookmarks to a text file; adds or removes attachments to a PDF; fixes a damaged PDF; and fills out PDF forms.
pdfinfo can extract information about PDF documents.
flpsed can add data to a PostScript document.
pdfmod is a simple application with a graphical interface that you can use to modify PDF documents.

[From missing-semester]

# 7. Debugging and Profiling
[lecture notes](https://missing.csail.mit.edu/2020/debugging-profiling/)

[perf - monitoring and analysis tool](https://www.tecmint.com/perf-performance-monitoring-and-analysis-tool-for-linux/)

# 8. Metaprogramming
Make is a build tool. It can be really useful for simplifying some common tasks.
It takes into account dependencies (eg, if some deps are not changed it will not execute that part of the code)
- main file is `makefile`
- https://linoxide.com/how-tos/linux-make-command-examples/
- [SO | why-use-make-over-a-shell-script](https://stackoverflow.com/questions/3798562/why-use-make-over-a-shell-script)
  - [SO | the case agains make](https://unix.stackexchange.com/questions/496793/script-or-makefile-to-automate-new-user-creation/497601#497601)
