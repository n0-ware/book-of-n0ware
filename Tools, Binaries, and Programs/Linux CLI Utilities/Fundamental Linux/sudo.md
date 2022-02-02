# sudo
## Description

`sudo` allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. The invoking user's real (_not_ effective) user ID is used to determine the user name with which to query the security policy.

**Related**
- [Elevated Linux Privileges](../../../Knowledge%20Base/Linux%20Fundamentals/10%20Elevated%20Linux%20Privileges.md)
- [Managing Sudo](../../../Knowledge%20Base/Linux%20Fundamentals/10%20Elevated%20Linux%20Privileges.md)
- [su](su.md)
- [visudo](visudo.md)
## Syntax

```
sudo [user (optional)] [command]
```

By default, using the `sudo` command followed by another command invokes that command as the `root` user. You can alternatively provide another username with `sudo` to run the command as that user. In either case, you must provide the password for that user to run the command. The default timeout until you must provide the password again is five minutes. 

Below, I use `id` as the user `kali` then provide `sudo` before it to run `id` as `root`. Spot how the ID changes. 

```
┌──(kali㉿kali)-[~/Documents/GitHub/course-notes]
└─$ id                                                             

uid=1000(kali) gid=1000(kali) 
                 
┌──(kali㉿kali)-[~/Documents/GitHub/course-notes]
└─$ sudo id
uid=0(root) gid=0(root) 
```

To list the current `sudo` privileges of your user, use the `-l` flag. 

```
┌──(kali㉿kali)-[~]
└─$ sudo -l
Matching Defaults entries for kali on kali:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin,
    use_pty

User kali may run the following commands on kali:
    (ALL : ALL) ALL
```

To login as the root user, provide the `-i` flag or use `sudo su`

```
┌──(kali㉿kali)-[~]
└─$ whoami 
kali
                  
┌──(kali㉿kali)-[~]
└─$ sudo -i

┌──(root💀kali)-[~]
└─# whoami
root
                  
┌──(root💀kali)-[~]
└─# exit
                  
┌──(kali㉿kali)-[~]
└─$ sudo su

┌──(root💀kali)-[/home/kali]
└─# whoami
root
```

## Managing Sudoers

- See [Managing Sudoers](../../../Knowledge%20Base/Linux%20Fundamentals/10%20Elevated%20Linux%20Privileges.md#managing-sudo)and [visudo](visudo.md).
