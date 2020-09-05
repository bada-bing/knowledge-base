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

## Symbolic Links
- `ln -s`
	- make (sybmolic) links between files (makes symlinks)
	- Hardlink vs Symlink [difference - SO link](https://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link)
  	- Symbolic Links should NOT be used with relative paths!
  	- https://www.moreofless.co.uk/linux-difference-soft-symbolic-link-and-hard-link/
