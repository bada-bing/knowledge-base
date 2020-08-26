Security Principles
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
