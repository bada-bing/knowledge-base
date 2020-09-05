# Permissions

In prompt `#` means I am running the following command as a root
- opposite to `$` (which is not-root user)

Desired is `sudo -i` or "initial login" (equivalent to `su -` and `sudo su -`), which tells sudo to start a shell and process the normal login scripts, e.g. .profile, .login, .bash_profile, etc.
- "sudo -i" does, in fact, give you a shell, AND it simulates a login the proper way. "sudo bash" suffers from the same environment problems as "sudo su"

If you don't need to go through "login" then 'sudo -s' will also work and just start up a new environment rather than login then env. Eg, `sudo -s` will drop you into a root shell and 'sudo -u foo -s' will drop you into a shell for user 'foo'.  Again without the login (.profile & .login).  I recommend using "sudo -c 'command'", "sudo -s" and "sudo -u foo -sH" (-H sets the homedir for the user as well).


# Security Principles
By default, Linux distinguishes between several account types in order to isolate processes and workloads. Linux has four types of accounts:

root
System
Normal
Network.
For a safe working environment, it is advised to grant the minimum privileges possible and necessary to accounts, and remove inactive accounts.

root is the most privileged account on a Linux/UNIX system. This account has the ability to carry out all facets of system administration, including adding accounts, changing user passwords, examining log files, installing software, etc. Utmost care must be taken when using this account. It has no security restrictions imposed upon it.

When you are signed in as, or acting as root, the shell prompt displays '#' (if you are using bash and you haven’t customized the prompt as we discuss elsewhere in this course). This convention is intended to serve as a warning to you of the absolute power of this account.

root privileges are required to perform operations such as:

Creating, removing and managing user accounts
Managing software packages
Removing or modifying system files
Restarting system services.
Regular account users of Linux distributions might be allowed to install software packages, update some settings, use some peripheral devices, and apply various kinds of changes to the system. However, root privilege is required for performing administration tasks such as restarting services, manually installing packages and managing parts of the filesystem that are outside the normal user’s directories.

sudo has the ability to keep track of unsuccessful attempts at gaining root access. Users' authorization for using sudo is based on configuration information stored in the /etc/sudoers file and in the /etc/sudoers.d directory.

A message such as the following would appear in a system log file (usually /var/log/secure) when trying to execute sudo bash without successfully authenticating the user:


Linux is considered to be more secure than many other operating systems because processes are naturally isolated from each other. One process normally cannot access the resources of another process, even when that process is running with the same user privileges. Linux thus makes it difficult (though certainly not impossible) for viruses and security exploits to access and attack random resources on a system.

More recent additional security mechanisms that limit risks even further include:

Control Groups (cgroups)
Allows system administrators to group processes and associate finite resources to each cgroup.
Containers
Makes it possible to run multiple isolated Linux systems (containers) on a single system by relying on cgroups.
Virtualization
Hardware is emulated in such a way that not only processes can be isolated, but entire systems are run simultaneously as isolated and insulated guests (virtual machines) on one physical host.

Linux limits user access to non-networking hardware devices in a manner that is extremely similar to regular file access. Applications interact by engaging the filesystem layer (which is independent of the actual device or hardware the file resides on). This layer will then open a device special file (often called a device node) under the /dev directory that corresponds to the device being accessed. Each device special file has standard owner, group and world permission fields. Security is naturally enforced just as it is when standard files are accessed.

Hard disks, for example, are represented as /dev/sd*. While a root user can read and write to the disk in a raw fashion, for example, by doing something like:

 $ echo hello world > /dev/sda1

The standard permissions as shown in the figure, make it impossible for regular users to do so. Writing to a device in this fashion can easily obliterate the filesystem stored on it in a way that cannot be repaired without great effort, if at all. The normal reading and writing of files on the hard disk by applications is done at a higher level through the filesystem, and never through direct access to the device node.


Originally, encrypted passwords were stored in the /etc/passwd file, which was readable by everyone. This made it rather easy for passwords to be cracked.

On modern systems, passwords are actually stored in an encrypted format in a secondary file named /etc/shadow. Only those with root access can modify/read this file.


Summary

The root account has authority over the entire system.
root privileges may be required for tasks, such as restarting services, manually installing packages and managing parts of the filesystem that are outside your home directory.
In order to perform any privileged operations such as system-wide changes, you need to use either su or sudo.
Calls to sudo trigger a lookup in the /etc/sudoers file, or in the /etc/sudoers.d directory, which first validates that the calling user is allowed to use sudo and that it is being used within permitted scope.
One of the most powerful features of sudo is its ability to log unsuccessful attempts at gaining root access. By default, sudo commands and failures are logged in /var/log/auth.log under the Debian family and /var/log/messages in other distribution families.
One process cannot access another process’ resources, even when that process is running with the same user privileges.
Using the user credentials, the system verifies the authenticity and identity.
The SHA-512 algorithm is typically used to encode passwords. They can be encrypted, but not decrypted.
Pluggable Authentication Modules (PAM) can be configured to automatically verify that passwords created or modified using the passwd utility are strong enough (what is considered strong enough can also be configured).
Your IT security policy should start with requirements on how to properly secure physical access to servers and workstations.
Keeping your systems updated is an important step in avoiding security attacks.

# File Ownership & File Permissions
Files have three kinds of permissions: read (r), write (w), execute (x).
These are generally represented as in `rwx`. These permissions affect three groups of owners: user/owner (u), group (g), and others (o).

As a result, you have the following three groups of three permissions:
rwx: rwx: rwx
 u:   g:   o

- `chown` - change user ownership of a file or directory
- `chgrp`  - change group ownership
- `chmod` - change the permissions on the file, which can be done separately for owner, group and the rest of the world (often named as other)

This is done with a simple algorithm, and a single digit suffices to specify all three permission bits for each entity. This digit is the sum of:
- 4 if read permission is desired     [3rd bit]
- 2 if write permission is desired    [2nd bit]
- 1 if execute permission is desired. [1st bit]
Thus, 7 means read/write/execute, 6 means read/write, and 5 means read/execute.
When you apply this to the chmod command, you have to give three digits for each degree of freedom, such as in:

- `$ chmod 755 somefile` - change permissions
- `ls -l somefile` - check permissions


# User Administration
**Users** have Unique ID (uid); integer; for normal users uid is > 1000
**Groups** are used for organizing users - collections of accounts with shared permissions; every group has gid
- `/etc/group` - shows a list of groups and their memebers
- default group has the same id as user's id
- can be found in /etc/passwd and /etc/group
- every user belongs to the default or primary group
- Groups are used to establish a set of users who have common interests for the purposes of access rights, privileges, and security considerations.
- Permissions on various files and dirs can be modified at the group level

To manage users on the system:
- `useradd` and `userdel` to add and del users
- `groupadd` and `groupdel` to add/del groups
- `id` - gives basic info about the user

- The `root` - superuser account
- you can use the `sudo` feature to assign more limited privileges to user accounts:
* Only on a temporary basis
* Only for a specific subset of commands.

When assigning elevated privileges, you can use the command `su` (switch or substitute user) to launch a new shell running as another user (you must type the password of the user you are becoming). Most often, this other user is root, and the new shell allows the use of elevated privileges until it is exited. It is **almost always** a bad (dangerous for both security and stability) practice to use `su` to become root. Resulting errors can include deletion of vital files from the system and security breaches.

Granting privileges using `sudo` is less dangerous and is preferred. By default, sudo must be enabled on a per-user basis. However, some distributions (such as Ubuntu) enable it by default for at least one main user, or give this as an installation option.

To execute just one command with root privilege type `sudo <command>`. When the command is complete, you will return to being a normal unprivileged user.

sudo configuration files are stored in the `/etc/sudoers` file and in the `/etc/sudoers.d/` directory. By default, the `sudoers.d` directory is empty.

By convention, most systems are set up so that the **root user** has a pound sign (`#`) as their prompt. Normal user will have `$`

# Summary
The root account has full access to the system. It is never sensible to grant full root access to a user.
You can assign root privileges to regular user accounts on a temporary basis using the `sudo` command.
The shell program (bash) uses multiple startup files to create the user environment. Each file affects the interactive environment in a different way.
`/etc/profile` provides the global settings.
Advantages of startup files include that they customize the user's prompt, set the user's terminal type, set the command-line shortcuts and aliases, and set the default text editor, etc.
An environment variable is a character string that contains data used by one or more applications. The built-in shell variables can be customized to suit your requirements.
The history command recalls a list of previous commands, which can be edited and recycled.
In Linux, various keyboard shortcuts can be used at the command prompt instead of long actual commands.
You can customize commands by creating aliases. Adding an alias to ˜/.bashrc will make it available for other shells.
File permissions can be changed by typing chmod permissions filename.
File ownership is changed by typing chown owner filename.
File group ownership is changed by typing chgrp group filename.
