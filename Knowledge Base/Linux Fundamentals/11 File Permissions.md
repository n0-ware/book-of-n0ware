# File Permissions
## Table of Contents

- [Permissions](#Permissions)
	- [Files](#Files)
	- [Directories](#Directories)
	- <a href="#numeric">Numeric Representation</a>
- <a href="#owner-group">Owners and Groups</a>
- <a href="#change-perms">Changing Permissions</a>
- <a href="#change-og">Changing Owners and Groups</a>

## Description

The permissions on a *Linux* file system are essential for understanding how users and processes interact with the files and folders on the system, both for a proper user experience and system functionality. Perhaps more so, however, they help protect system security. An example is the world-readable [passwd](09%20Users%20and%20Groups.md#passwd) and the root-owned [shadow](09%20Users%20and%20Groups.md#shadow). They function together, but have different permissions, and contain different information. 

The job of a *Linux* systems administrator and security professional is to ensure that the right users have the right access and that the wrong users cannot access sensitive files, such as configurations, that could enable them to elevate their privileges higher than they should be. In a non-malicious situation, this is simply a bad idea. But for a malicious actor, this can mean complete system compromise. 

These permissions, and the users or groups they apply to, can be changed with the right commands under the right circumstances. 

### Permissions

#### Files
Nearly every resource from files to directories, devices and services, network communications, and mounted drives are all represented somewhere on the filesystem. Among those familiar with the file system, it is common to say that "everything is a file." For example, a text containing IP addresses, and the binary that controls the [Nmap](../../Tools,%20Binaries,%20and%20Programs/Information%20Gathering/Network%20Reconnaissance/Nmap.md) program code are both files. 

There are three categories of users in *Linux* &mdash; u, g, and o.

- **u**ser (owner)
- **g**roup(noted by a users GID)
- **o**ther (or everyone)

For each of the three categories, there are three sets of "access" types &mdash; r, w, and x

- **r**ead, meaning the file can be rea/copied
- **w**rite, meaning the file can be written to/modified
- e**x**ecute, meaning the file can be run (executed)

Each of these three groups has all, some, or none of the three types of access or "rights" to the file, broken into three sets of three dashes. A file with no permissions would have nine dashes, `---------`, but this will rarely if ever be the case. At a minimum, the file will have one `r` to be read-only by the owner, as is the case for many root-owned files. 

These permissions are visible with the [`ls -l`](02%20Listing%20Files.md#ls) command for "long listing."

```
-rw-r-xr-- 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
```

In this case, the permissions look like this. 

| User (u) | Group (g) | Other (o) |
| :-: | :-: | :-: |
| rw- | r-x | r-- |
| Read/Write | Read/Execute | Read only | 

#### Directories

Directories act nearly the same but with slight differences. 

An `r` gives the user the ability to read what the files inside the directory are, such as with `ls`, but not necessarily access the files themselves. 

The `w` allows for modifying directory contents, such as adding or deleting files, but not necessarily modifying the files themselves. This could mean you may add or delete a file but not change the contents once added. 

Where the `x` permission for a file allows it to be run (executed), an `x` in a directory means that it can be navigated into, such as with `cd`. 

This can cause some interesting styles of interaction. For example, a directory without `r` with with `x` would mean a user can interact with the files in a directory, but only if they are known by name, as the user cannot list the files inside. 

#### Numeric Representation <a id="numeric"></a>

These permissions can be represented numerically based on the concept of binary "on" and "off". If a bit is "on" it has a "1" and "off" means "0". Since each file has three sets of permissions, there are three possible sets of binary and its base-10 equivalent.

Understanding precisely how binary works is out of the scope of this note, but for example, consider the permissions `rwxrw-r--`. The three sets of permissions, their binary representation, and number in base-10 are:

| Permissions | Binary | Base-10 Conversion | 
| :-: | :-: | :-: |
| rwx | 111 | 7 |
| rw- | 110 | 6 |
| r-- | 100 | 5 | 

Each of the three types of permissions occupies a space in this binary triplet. The combinations can represent any combination of three 1's and 0's from `000` to `111`. Since each permissions setting occupies a specific location in the triplet, they each have a numeric value. 

- `r` = 4
- `w` = 2
- `x` = 1

Knowing these values allows for the various combinations of permissions, for example. 

- 7 = 4 + 2 + 1 = read, write, execute (full permissions)
- 3 = 2 + 1 = write and execute
- 5 = 4 + 1 = read and execute

There is only one possible way of reaching every number between 1 and 7, making it easy to determine which combination of permissions each number stands for. 

Use this in combination with the [chmod](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/chmod.md) command to adjust user permissions. 

#### Changing Permissions <a id="change-perms"></a>

File permissions are managed with the `chmod` command. See [chmod](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/chmod.md)

### Owners and Groups <a id="owner-group"></a>

In addition to permissions, each file has a "user" and a "group" assigned to it. In the file below, the user and group are both `demouser`. 

```
-rw-r-xr-- 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
```

The "owner" is who the first set of `rwx` applies to, the group the second, and everyone else, not either "user" or "group" is who the third set applies to. For example, if I own a file that has a command that needs to interact with this file, I have `rw` permissions, but anyone else that owns a file and tries to interact with my file only has `r` permissions. This is how the "owner" and "group" settings affect file permissions. 


#### Changing Owners and Groups <a id="change-og"></a>

File membership, or the "owner" and "group," is managed by the `chown` command. See [chown](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/chown.md)

### Special Permissions <a id="special-perms"></a>

Two special permissions apply to the e**x**ecutable permission of files. They are the `setuid` and `setgid` bits. The symbol for this bit is either an uppercase or lowercase `s`. This bit takes the place of the `x` bit in the permissions list. It will be lowercase if the `x` is also set, and uppercase if the `x` bit is missing. 

The purpose of this bit is to allow ***any*** user to execute the file with the permissions of the owner or the owner's group, depending on which set of permissions the `s` appears in. This may be handy if I, as a low privileged user, need to give access to a benign executable to someone else but don't want to share my password or increase their level of permissions. 

Consider if this is applied to sensitive files or binaries, like those used to manage the file system or add users, like `/etc/passwd` or [useradd](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#useradd). If anyone can access a file designed to fundamentally alter the system or create their own user, that can lead to a  major security breach. A low-privileged user able to create a user could create their own user with higher privileges. Consider if any user could use the [visudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/visudo.md) command, they could alter the "sudoer" privileges for anyone. 

#### setuid

Let's use the `whoami` command as an example of the `setuid` bits impact. According to the man page, running `whoami`  will *"print the user name associated with the current effective user ID"* The "effective user-id" is also known as the `eid`. If `whoami` were to be owned by `root` and set with the `setuid` bit, it will then execute as `root` every time. Let's create a copy of this binary and make some modifications. 

```
┌──(kali㉿kali)-[~]
└─$ sudo cp /usr/bin/whoami /usr/bin/whoamiroot                   

┌──(kali㉿kali)-[~]
└─$ whoamiroot  
kali
                    
┌──(kali㉿kali)-[~]
└─$ sudo chown root:kali /usr/bin/whoamiroot 
                    
┌──(kali㉿kali)-[~]
└─$ sudo chmod u+s /usr/bin/whoamiroot      
                    
┌──(kali㉿kali)-[~]
└─$ ls -la /usr/bin/whoamiroot 
-rwsr-xr-x 1 root kali 35616 Jan 19 22:46 /usr/bin/whoamiroot
                    
┌──(kali㉿kali)-[~]
└─$ whoamiroot
root
```

While this is a benign example, a common example is a snipped of *Python* code with the `setuid` bit set that is editable by a normal user. That user could edit the code, and run it as root, and with a basic level of *Python* knowledge, wreak havoc on a system. 

#### setgid

Similar to [setuid](#setuid), the `setgid` command applies to the group instead of the user, meaning that all files with the group `x` bit set to `s` will run as that group. Let's test this with the `id` program, which will list out the effective group ID or `GID` when run. We will use a similar process as the `whoami` example in `setuid` for this, creating a copy of the binary, editing the owner, adding the `setgid` bit, and then running the program. 

```
                    
┌──(kali㉿kali)-[~/setuiddir]
└─$ id    
uid=1000(kali) gid=1000(kali) groups=1000(kali)

┌──(kali㉿kali)-[~/setuiddir]
└─$ sudo cp /usr/bin/id /usr/bin/idroot
                    
┌──(kali㉿kali)-[~/setuiddir]
└─$ sudo chown kali:root /usr/bin/idroot 
                    
┌──(kali㉿kali)-[~/setuiddir]
└─$ sudo chmod g+s /usr/bin/idroot      
                    
┌──(kali㉿kali)-[~/setuiddir]
└─$ idroot
uid=1000(kali) gid=1000(kali) egid=0(root) groups=0(root)        
```

Notice how in the first run of `id`, there is no `eid`, but in the second, our `id` is root. This is the effect of the `setgid` bit. 

#### stickybit

The "sticky bit" refers to a directory-focused bit in the permissions line that shows up as a `t` and prevents anyone from deleting files, except for the owner of the file or the owner of the directory. This is great for shared files, where many have access but one wants control over the contents of the directory, or to prevent others from manipulating files they don't own. 

Consider a situation where people were uploading "proofs" as text files to a shared directory, where permissions don't matter except for you don't want other people deleting other's files. The `/tmp` directory is such a directory, where most have access to it, but the owner of the directory may want control. 

```
┌──(demouser㉿kali)-[~]
└─$ ls -l
total 4
drwxr-xr-t 2 demouser demouser 4096 Jan 19 23:36 sharedDir
```

Notice the small `t` in the "everyone" or "other" section of the permissions line. 



