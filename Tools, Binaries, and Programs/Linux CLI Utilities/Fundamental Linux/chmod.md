# chmod
## Description

The `chmod` command is used to change the [permissions](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#Permissions) of a file or directory. For information on the users and groups, see [owners and groups](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#Owner%20and%20Group%20a%20id%20owner-group%20a)

The concepts [setuid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setuid) and [setgid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setgid) are related to this. 

## Syntax

```
chmod [options] file
```

The `-R` flag makes it recursive if used on a directory. 

There are two ways to use the `chmod` command. The first is with character representation for the various user and group permissions, the second files on understanding the [Numeric Representation](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#Numeric%20Representation%20a%20id%20numeric%20a) of file permissions

### Characters

The owner, group, and other are represented by &mdash; o, g, and u. Each permissions setting is represented by &mdash; r, w, and x. Combining these with an operator will create a new or modified set of permissions. The possible operators are &mdash; `+` for add, `-` for remove, or `=` for replacing with the new set of permissions. Separate each set of characters with a comma, and you perform all the modifications in one command

In practice, this comes out to a set of characters and operators that change the permissions of a file. For example, imagine this change. 

- Set the **user** permissions to read and write
- Add write permissions to the group
- Remove read and write permissions from everyone else

The combination ends up as `u=rw,g+w,o-rw`. For example, see the command below, modifying a file that has the permissions, `rwx---r-x` or `705` permissions. 

```
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt                                     -rwx---r-x 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
                  
┌──(demouser㉿kali)-[~]
└─$ chmod u=rw,g+w,o-rw permissionsfile.txt
                  
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt 
-rw--w---x 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
      
```

### Numbers

An alternative to using characters and operators is using the [Numeric Representation](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#Numeric%20Representation%20a%20id%20numeric%20a)  of the permissions. Note that when using the numeric representation of permissions, you must explicitly set the permissions each time. You cannot add single permissions, remove one, set permissions only for the owner, and so forth. It is all or nothing. 

The syntax is the same as using characters, but with numbers. 

```
chmod [options] [file]
```

For example, setting a file to full permissions:

```
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt              
-rw--w---x 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt

┌──(demouser㉿kali)-[~]
└─$ chmod 777 permissionsfile.txt          
                  
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt 
-rwxrwxrwx 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
```

A common setting for `SSH` keys is `400`, meaning readable only by the owner. 

```
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt 
-rwxrwxrwx 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
                  
┌──(demouser㉿kali)-[~]
└─$ chmod 400 permissionsfile.txt 
                                                             
┌──(demouser㉿kali)-[~]
└─$ ls -l permissionsfile.txt 
-r-------- 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt

```

### setuid

To set the `setuid` bit, we use the `+s` option for the "user." 

```
chmod u+s [file]
```

For more see [setuid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setuid)

### setgid

To set the `setgid` bit, we use the `+s` option for the "group."

```
chmod u+s [file]
```

For more see [setgid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setgid)