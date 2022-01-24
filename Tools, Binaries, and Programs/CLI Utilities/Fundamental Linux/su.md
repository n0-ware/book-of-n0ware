# su
## Description
The `su` command may be used to switch users, run a command as a specific user, or log in as the root user. 

## Syntax

***Common arguments:***
- `-l` &mdash; Login as another user 
- `-c "[command]"` &mdash; Run a specific command as the user but do not login 
- `-s [shell]` &mdash; Specify a shell on login

Without any other commands, the default is to log in as the `root` user and requires `sudo` before it as it is a privileged command. 

```
┌──(kali㉿kali)-[~]
└─$ sudo su                                                                      
┌──(root💀kali)-[/home/kali]
└─# whoami
root
```

Running `su` without `sudo` will ask for the root password, which is deactivated by default on some *Linux* distributions, but running it with `sudo` prompts us for our password, and if we are "sudoer" on the system, it will allow us to run the command as root. 

Logging in as another user requires the `-l` flag:

```
┌──(kali㉿kali)-[~]
└─$ su -l demouser
Password: 

┌──(demouser㉿kali)-[~]
└─$ whoami
demouser
```

`su` may also be used to run single commands with `-c "[command]"`

```
┌──(kali㉿kali)-[~]
└─$ su -l demouser -c "whoami"
Password: 
demouser
                                                                                     
┌──(kali㉿kali)-[~]
└─$ whoami
kali
```