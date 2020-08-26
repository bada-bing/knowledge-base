# File System

The filesystem tree starts at what is often called the root directory (or trunk, or /).
The  Filesystem Hierarchy Standard (FHS) provides Linux developers and system administrators a standard directory structure for the filesystem.
Partitions help to segregate files according to usage, ownership, and type.
Filesystems can be mounted anywhere on the main filesystem tree at a mount point. Automatic filesystem mounting can be set up by editing /etc/fstab.
NFS (Network File System) is a useful method for sharing files and data through the network systems.
Filesystems like /proc are called pseudo filesystems because they exist only in memory.
/root (slash-root) is the home directory for the root user.
/var may be put in its own filesystem so that growth can be contained and not fatally affect the system.
/boot contains the basic files needed to boot the system.
patch is a very useful tool in Linux. Many modifications to source code and configuration files are distributed with patch files, as they contain the deltas or changes to go from an old version of a file to the new version of a file.
File extensions in Linux do not necessarily mean that a file is of a certain type.
cp is used to copy files on the local machine, while rsync can also be used to copy files from one machine to another, as well as synchronize contents.
gzip, bzip2, xz and zip are used to compress files.
tar allows you to create or extract files from an archive file, often called a tarball. You can optionally compress while creating the archive, and decompress while extracting its contents.
dd can be used to make large exact copies, even of entire disk partitions, efficiently.

In Linux (and all UNIX-like operating systems) it is often said **“Everything is a file”**, or at least it is treated as such. This means whether you are dealing with normal data files and documents, or with devices such as sound cards and printers, you interact with them through the same kind of Input/Output (I/O) operations. This simplifies things: you open a “file” and perform normal operations like reading the file and writing on it (which is one reason why text editors, which you will learn about in an upcoming section, are so important).

the filesystem is structured like a tree. The tree is usually portrayed as inverted, and starts at what is most often called the root directory, which marks the beginning of the hierarchical filesystem and is also sometimes referred to as the trunk, or simply denoted by /.

Linux supports a number of native filesystem types, expressly created by Linux developers, such as: `ext3, ext4, squashfs, btrfs`
It also offers implementations of filesystems used on other alien operating systems, such as those from:
Windows (ntfs, vfat), SGI (xfs), IBM (jfs), MacOS (hfs, hfs+).
Many older, legacy filesystems, such as FAT, are also supported.
It is often the case that more than one filesystem type is used on a machine, based on considerations such as the size of files, how often they are modified, what kind of hardware they sit on and what kind of access speed is needed, etc. The most advanced filesystem types in common use are the journaling varieties: ext4, xfs, btrfs, and jfs. These have many state-of-the-art features and high performance, and are very hard to corrupt accidentally.

As we discussed earlier, each filesystem on a Linux system occupies a hard disk partition. Partitions help to organize the contents of disks according to the kind and use of the data contained. For example, important programs required to run the system are often kept on a separate partition (known as root or /) than the one that contains files owned by regular users of that system (/home). In addition, temporary files created and destroyed during the normal operation of Linux may be located on dedicated partitions. One advantage of this kind of isolation by type and variability is that when all available space on a particular partition is exhausted, the system may still operate normally.

## Mount Points
Before you can start using a filesystem, you need to mount it to the filesystem tree at a mount point. This is simply a directory (which may or may not be empty) where the filesystem is to be attached (mounted). Sometimes, you may need to create the directory if it does not already exist.

The mount command is used to attach a filesystem (which can be local to the computer or, as we shall discuss, on a network) somewhere within the filesystem tree. The basic arguments are the device node and mount point. For example,

`sudo mount /dev/sda5 /home`
will attach the filesystem contained in the disk partition associated with the /dev/sda5 device node, into the filesystem tree at the /home mount point. There are other ways to specify the partition other than the device node, such as using the disk label or UUID.

`sudo umount /home`

Note the command is `umount`, not unmount!
If you want it to be automatically available every time the system starts up, you need to edit /etc/fstab accordingly (the name is short for filesystem table).
Typing mount without any arguments will show all presently mounted filesystems.
The command df -Th (disk-free) will display information about mounted filesystems, including the filesystem type, and usage statistics about currently used and available space.

The most common network filesystem is named simply NFS (the Network Filesystem). This allows the users to log in to different computers, yet still have access to the same files and resources.

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

# Back Up
`rsync` is more efficient than `cp`, because it checks if the file being copied already exists.
The contents of sourcefile will be copied to destinationfile.
If the file exists and there is no change in size or modification time, rsync will avoid an unnecessary copy and save time.
Furthermore, because rsync copies only the parts of files that have actually changed, it can be very fast.

- `rsync` can also be used to copy files from one machine to another.
Locations are designated in the `target:path` form, where target can be in the form of `someone@host`.
The `someone@` part is optional and used if the remote user is different from the local user.

- `rsync` is very efficient when recursively copying one directory tree to another, because only the differences are transmitted over the network.
One often synchronizes the destination directory tree with the origin, using the `-r` option to recursively walk down the directory tree copying all files and directories below the one listed as the source.

- Very useful way to back up a project directory might be to use the following command:
`$ rsync -r project-X archive-machine:archives/project-X`

- Note that rsync can be very destructive! Accidental misuse can do a lot of harm to data and programs, by inadvertently copying changes to where they are not wanted. Take care to specify the correct options and paths. It is highly recommended that you first test your rsync command using the -dry-run option to ensure that it provides the results that you want.

A good combination of options is shown in:
`$ rsync --progress -avrxH  --delete sourcedir destdir`

# Compression
Linux uses a number of methods to perform this compression, including:

Command	Usage
`gzip`	The most frequently used Linux compression utility
`bzip2`	Produces files significantly smaller than those produced by gzip
`xz`	The most space-efficient compression utility used in Linux
`zip`	Is often required to examine and decompress archives from other operating systems

These techniques vary in the efficiency of the compression (how much space is saved) and in how long they take to compress; generally, the more efficient techniques take longer. Decompression time does not vary as much across different methods.

In addition, the tar utility is often used to group files in an archive and then compress the whole archive at once.

`gzip` is the most often used Linux compression utility. It compresses very well and is very fast. The following table provides some usage examples:
- `gzip *`	Compresses all files in the current directory; each file is compressed and renamed with a .gz extension
- `gzip -r projectX`	Compresses all files in the projectX directory, along with all files in all of the directories under projectX
- `gunzip foo`	De-compresses foo found in the file foo.gz. Under the hood, the gunzip command is actually the same as gzip –d

`bzip2` has a syntax that is similar to gzip but it uses a different compression algorithm and produces significantly smaller files, at the price of taking a longer time to do its work. Thus, it is more likely to be used to compress larger files.

Examples of common usage are also similar to gzip:
- `bzip2 *`	Compresses all of the files in the current directory and replaces each file with a file renamed with a .bz2 extension
- `bunzip2 *.bz2`	Decompresses all of the files with an extension of .bz2 in the current directory. Under the hood, bunzip2 is the same as calling bzip2 -d

`xz` is the most space efficient compression utility used in Linux and is now used to store archives of the Linux kernel. Once again, it trades a slower compression speed for an even higher compression ratio.

`xz *`	Compresses all of the files in the current directory and replaces each file with one with a .xz extension
`xz foo`	Compresses the file foo into foo.xz using the default compression level (-6), and removes foo if compression succeeds
`xz -dk bar.xz`	Decompresses bar.xz into bar and does not remove bar.xz even if decompression is successful
`xz -dcf a.txt b.txt.xz > abcd.txt`	Decompresses a mix of compressed and uncompressed files to standard output, using a single command
`$ xz -d *.xz`	Decompresses the files compressed using xz

`zip` is often required to examine and decompress archives from Windows. It is a legacy program.
- `zip backup *`	Compresses all files in the current directory and places them in the file backup.zip
- `zip -r backup.zip` ~	Archives your login directory (~) and all files and directories under it in the file backup.zip
- `unzip backup.zip`	Extracts all files in the file backup.zip and places them in the current directory

[DONT experiment with following command as it can erase HDD]
The `dd` program is very useful for making copies of raw disk space. For example, to back up your Master Boot Record (MBR) (the first 512-byte sector on the disk that contains a table describing the partitions on that disk), you might type:
- `$ dd if=/dev/sda of=sda.mbr bs=512 count=1`

## Symbolic Links
- `ln -s`
	- make (sybmolic) links between files (makes symlinks)
	- Hardlink vs Symlink [difference - SO link](https://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link)
  	- Symbolic Links should NOT be used with relative paths!
  	- https://www.moreofless.co.uk/linux-difference-soft-symbolic-link-and-hard-link/
