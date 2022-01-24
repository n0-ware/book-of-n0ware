# Elevated Linux Privileges
###### Tags[^1]

[^1]: #linux #fundamental #sudo #users 

## Table of Contents

- <a href="#sudoers">Sudoers</a>
- <a href="#managing-sudo">Managing Sudoers</a>
<a href="#"></a>
<a id=""></a>

**Related:**
- [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md)
- [su](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/su.md)
- [visudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/visudo.md)

### Sudoers <a id="sudoers"></a>

The users in linux that have elevated privileges are considered "sudoers." These users have either full or partial use of the `sudo` command (see [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md)) to run commands that either intrinsically or through configuration require elevated privileges. 

Note that `sudo` can be used to perform commands as another user than root, see the link for more arguments related to the `sudo` command, including listing sudoers 

An easy way to distinguish if you are regular or superuser on the command line, except for the obvious `whoami`, is that regular users typically have a `$` before the command prompt on the shell, and `root` users have a `#`

It is worth noting that the `root` user can access any account, even deactivated ones. 

### Managing Sudoers <a id="managing-sudo"></a>

The list of "sudoers" is kept in the `/etc/sudoers` file, which is protected and owned by the `root` user. 

```
┌──(root💀kali)-[~]
└─# ls -la /etc/sudoers
-r--r----- 1 root root 1585 Dec 18 08:55 /etc/sudoers
```

To edit this file, you must use the [visudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/visudo.md) command. There are a lot of options in this file, but two of the most important sections are the defaults information at the top of the file. Editing the `secure_path` file allows you to specify the `$PATH` variable that the [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) command uses when ran. 
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin>
Defaults        use_pty
```

Second is the more important area. This is where we can define the user privilege specifications and define commands that can be ran with `sudo` for a specific user.

```
# User privilege specification
root    ALL=(ALL:ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "@include" directives:

@includedir /etc/sudoers.d
```

Learn more about editing the `sudoers` file with `man visudo` or at [this link](https://www.maketecheasier.com/edit-sudoers-file-linux/). 

