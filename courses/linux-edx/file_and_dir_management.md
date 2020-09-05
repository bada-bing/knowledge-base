# Symbolic Links
Create symbolic link: `ln -s file1 file3`
`ls -li file1 file3`

Symbolic links take no extra space on the filesystem (unless their names are very long).
They can easily be modified to point to different places.
An easy way to create a shortcut from your home directory to long pathnames is to create a symbolic link.

Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media, which may or may not be currently available or even exist.
In the case where the link does not point to a currently available or existing object, you obtain a dangling link.

# Globs
	- a sequence of literal and wildcard characters used to match filepath
	- [explaining globs](https://gulpjs.com/docs/en/getting-started/explaining-globs)
	-  Opposite of wildcard character is literal character
	- / - separator
	- \\ - escape character
		- 'glob_with_uncommon_\\*_character.js'
			§ an example: star is here escaped so it is actual literal charcter
	- Special Characters: ** (to include nested folders), ! (negative)

# Directories
The `/bin` directory contains executable binaries, essential commands used to boot the system or in single-user mode, and essential commands required by all system users, such as `cat, cp, ls, mv, ps, rm`.
Likewise, the `/sbin` directory is intended for essential binaries related to system administration, such as fsck and shutdown. To view a list of these programs, type:  `ls /bin /sbin`
Commands that are not essential (theoretically) for the system to boot or operate in single-user mode are placed in the /usr/bin and /usr/sbin directories
istorically, this was done so /usr could be mounted as a separate filesystem that could be mounted at a later stage of system startup or even over a network. However, nowadays most find this distinction is obsolete. In fact, many distributions have been discovered to be unable to boot with this separation, as this modality had not been used or tested for a long time.
Thus, on some of the newest Linux distributions /usr/bin and /bin are actually just symbolically linked together, as are /usr/sbin and /sbin.

about directories
/bin - binaries
/lib - libraries
/etc - config files
/home - home dir of each user
/tmp - temporary dir
/var - files that change over time (lock files for package managers, log files, files that keep track about process ids)
/dev - devices
/sys -
/opt - some about 3rd party sw (not so important)

The `/dev` directory contains device nodes, a type of pseudo-file used by most hardware and software devices, except for network devices.
Contains entries which are created by the udev system, which creates and manages device nodes on Linux, creating them dynamically when devices are found. The /dev directory contains items such as:
`/dev/sda1` (first partition on the first hard disk)
`/dev/lp1` (second printer)
`/dev/random` (a source of random numbers).
`/dev/null` ❓

The `/var` directory contains files that are expected to change in size and content as the system is running (var stands for variable), such as the entries in the following directories:

- System log files: /var/log
- Packages and database files: /var/lib
- Print queues: /var/spool
- Temporary files: /var/tmp.
- Network services directories such as /var/ftp (the FTP service) and /var/www (the HTTP web service) are also found under /var.

The `/etc` directory is the home for system (system-wide) configuration files.
It contains no binary programs, although there are some executable scripts. For example, /etc/resolv.conf tells the system where to go on the network to obtain host name to IP address mappings (DNS). Files like passwd, shadow and group for managing user accounts are found in the /etc directory.
User-specific configuration files are always found under their home directory.

The `/boot` directory contains the few essential files needed to boot the system.
For every alternative kernel installed on the system there are **four files**:

 - vmlinuz The compressed Linux kernel, required for booting.
 - initramfs The initial ram filesystem, required for booting, sometimes called initrd, not initramfs.
 - config The kernel configuration file, only used for debugging and bookkeeping.
 - System.map Kernel symbol table, only used for debugging.
Each of these files has a kernel version appended to its name.

The Grand Unified Bootloader (GRUB) files such as `/boot/grub/grub.conf` or /boot/grub2/grub2.cfg are also found under the /boot directory.

The `/lib` contains libraries (common code shared by applications and needed for them to run) for the essential programs in /bin and /sbin. These library filenames either start with ld or lib. For example, /lib/libncurses.so.5.9.

One often uses removable media, such as USB drives, CDs and DVDs.
To make the material accessible through the regular filesystem, it has to be mounted at a convenient location.
Most Linux systems are configured so any removable media are automatically mounted when the system notices something has been plugged in.

While historically this was done under the `/media` directory, modern Linux distributions place these mount points under the `/run` directory.
For example, a USB pen drive with a label "myusbdrive" for a user name "student" would be mounted at `/run/media/student/myusbdrive`.

The `/mnt` directory has been used since the early days of UNIX for temporarily mounting filesystems.
These can be those on removable media, but more often might be network filesystems with NFS, which are not normally mounted.
Or these can be temporary partitions, or so-called loopback filesystems, which are files which pretend to be partitions.

The `/usr` directory tree contains theoretically non-essential programs and scripts (in the sense that they should not be needed to initially boot the system) and has at least the following sub-directories:

`/usr/include`	Header files used to compile applications
`/usr/lib`	Libraries for programs in /usr/bin and /usr/sbin
`/usr/lib64`	64-bit libraries for 64-bit programs in /usr/bin and /usr/sbin
`/usr/sbin`	Non-essential system binaries, such as system daemons
`/usr/share`	Shared data used by applications, generally architecture-independent
`/usr/src`	Source code, usually for the Linux kernel
`/usr/local`	Data and programs specific to the local machine. Subdirectories include bin, sbin, lib, share, include, etc.
`/usr/bin`	This is the primary directory of executable commands on the system
