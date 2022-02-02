# Linux User Management
###### Tags[^1]

[^1]: #users #linux #fundamental #passwords 
## Table of Contents
- [useradd](#useradd)
- [userdel](#userdel)
- [usermod](#usermod)
- [passwd](#passwd)
- [chage](#chage)

### useradd
##### Description

The command `useradd` creates a user in *Linux*. To create a user and home directory at the same time, add the `-m` flag. You must have superuser privileges to create a user in *Linux*. 

#### Syntax

```
useradd [args] [username]
```

- `-m` &mdash; Creates a home directory for the user. Default is `/home/[username]`. It also creates all the base files in the home directory
- `-g [GID]` &mdash; Add the user to the group `[GID]`
- `-s [shell]` &mdash; Specifies the shell for the user on creation
- `-d [directory name]` &mdash; Specifies the name of the home directory. You must specify the directory name and path, i.e., `/home/demohome`
- `-p` &mdash; Specify password on creation
- `-D` &mdash; Change the defaults for this command
And many more...

***Example***
```
┌──(root💀kali)-[/home/kali/Documents/GitHub/course-notes]
└─# useradd -m -d /home/demohome -s /usr/bin/zsh -p demo demouser 
                    
┌──(root💀kali)-[/home/kali/Documents/GitHub/course-notes]
└─# cat /etc/passwd | grep demouser
demouser:x:1002:1002::/home/demohome:/usr/bin/zsh
                    
┌──(root💀kali)-[/home/kali/Documents/GitHub/course-notes]
└─# cat /etc/shadow | grep demouser
demouser:demo:19011:0:99999:7:::
                    
┌──(root💀kali)-[/home/kali/Documents/GitHub/course-notes]
└─# ls /home
demohome  kali
                    
┌──(root💀kali)-[/home/kali/Documents/GitHub/course-notes]
└─# su -l demouser

┌──(demouser㉿kali)-[~]
└─$ whoami
demouser
```

***Printing default settings***
```
┌──(root💀kali)-[/etc/skel]
└─# useradd -D                                                   
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/sh
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no
```

***Editing default skeleton directories***

```
┌──(root💀kali)-[/etc/skel]
└─# mkdir Documents Downloads Pictures Videos Misc

┌──(root💀kali)-[/etc/skel]
└─# ls          
Documents  Downloads  Misc  Pictures  Videos
                    
┌──(root💀kali)-[/etc/skel]
└─# userdel -r demouser
userdel: demouser mail spool (/var/mail/demouser) not found
                    
┌──(root💀kali)-[/etc/skel]
└─# useradd -m -d /home/demohome -s /usr/bin/zsh -p demo demouser
                 
┌──(root💀kali)-[/etc/skel]
└─# ls /home/demohome 
Documents  Downloads  Misc  Pictures  Videos
```

### userdel
#### Description

To delete a user in *Linux*, use the `userdel` command followed by the name of the user to delete. To delete the home directory at the same time, add the `-r` flag. 

#### Syntax

```
userdel [args] [username]
```

***Example***

```
┌──(root💀kali)-[~]
└─# ls /home
demouser  kali

┌──(root💀kali)-[~]
└─# man userdel
                    
┌──(root💀kali)-[~]
└─# ls /home
kali
```

### usermod
#### Description

The `usermod` command is a system administration tool used to manage user settings. 

#### Syntax

```
usermod [args] [username]
```

- `-L` &mdash; Locks a user out of their account with a `!` in the `/etc/passwd` file. 
- `-s [shell]` &mdash; Change the default shell of a user
- `-a -G [groupname]` &mdash; Append a group to the users current group
	- For example, `sudo usermod -a -G sudo baduser` to create a backdoor superuser on a compromised system

> A user can be locked out of their account in several ways. One of them is changing the users default shell to `/sbin/nolgin` or `/bin/false`.

### passwd
#### Description

The `passwd` command can be used to set the password of a user on *Linux*

#### Syntax

```
passwd [args] [username]
```

- `-l` &mdash; Locks a user out of their account with a `!` in the `/etc/passwd` file. 
- `--status` &mdash; Get the status of a user

### chage

#### Description

The `change` command can be used to manage certain elements of a user's password, such as the expiration date.

#### Syntax

- `-E` &mdash; Change the expiration date on a user account
- `-m` &mdash; Set minimum expiration dates 
- `-M` &mdash;  Set maximum expiration days
- `-W` &mdash; Set warn days  
