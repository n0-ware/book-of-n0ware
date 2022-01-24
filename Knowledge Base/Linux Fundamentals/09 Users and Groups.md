# Users and Groups
> PEN-100 Plagarism warning
> 
> Edward Hartmann  
> January 18, 2022

###### Content Tags[^1]

[^1]: #users #linux #fundamental 

## Table of Contents

- <a href="#create">Creating a User</a>
- <a href="#delete">Deleting a User</a>
- <a href="#details">Details on Linux Users</a>
	- [passwd](#passwd)
	- [shadow a id etc-shadow a](#shadow%20a%20id%20etc-shadow%20a)
- <a href="#accounts">Managing User Accounts</a>
- <a href="#password">Managing User Passwords</a>
- <a href="#user-groups">User Groups</a>
- <a href="#whoami">Whoami</a>

- [Linux User Management](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md)

<a href="# "></a>
<a id=" "></a>
### Creating a User <a id="create"></a>

See [useradd](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#useradd)

### Deleting a User <a id="delete"></a>

See  [userdel](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#userdel)
### Managing User Accounts <a id="accounts"></a>

See [usermod](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#usermod)

### Managing User Passwords <a id="password"></a>

See [passwd](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#passwd) or [chage](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/Linux%20User%20Management.md#chage)
### Details on Linux Users <a id="details"></a>

The most common authentication schemes, and therefore storage of general user data, on a Linux System, is the combination of `/etc/passwd/` and `/etc/shadow` files. 

The `passwd` file stores information about the users and is designed to be world-readable as many utilities depend on reading it for a variety of reasons. To protect the sensitive authentication information, `passwd` stores a reference to the user's password that is actually contained in the `shadow` file as a "fingerprint" or [hash](../Concepts/General/Hashing.md) of the user's password. The `shadow` file is only accessible by high-privileged users. 

All of the details in these files are separated by colons `:`, which is very handy for separating with [cut](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/cut.md) and [awk](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/awk.md).


**Here are examples of the two. ** 

#### passwd
<a id="etc-passwd"></a>
```                                        
demouser:x:1002:1002::/home/demouser:/bin/sh
```

- The user `demouser` is stored in plaintext
- `x` informs the system and other users to look for the password in the `shadow` file. 
- Next is the user's` UID` or user id. 
- Paired with the `UID` is the `GID` or group id
- Between this and the next is the (currently empty and always optional) comment field, usually used for information
- After this is the users home directory, typically `/home/[username]`
- The final entry is the default shell environment for the user. 

> A user can be locked out of their account in several ways. One of them is changing the user's default shell to `/sbin/nolgin` or `/bin/false`.

#### shadow 
<a id="etc-shadow"></a>
```
demouser:$y$j9T$wbaVjnWWQFv6lhVhUZUMH0$Bv9156uBqTBE/6z/ek1NxUBSyZ1roi0.4kZC.dkwoy.:19011:0:99999:7:::
```

- The user `demouser` is stored in plain text. 
- Next is the encrypted password. The first portion is the encryption algorithm used, `$y$` in this case. The next portion is the actual encrypted password. A `!` or `*` in this field means the user is locked out
- After that is a timestamp related to the last time a password was changed. 
- Next is a number that controls the minimum date required between password changes, `0` in this case, which is the default. 
- `99999` represents the maximum date this password is valid. By default, this 273 years. 
- The final number, `7`, is the days ahead of a required password change the system will issue a warning. 

### User Groups <a id="user-groups"></a>

Similar to `passwd` and `shadow`, user groups are stored in `/etc/group`

```
wireshark:x:120:kali,root
```

- `wireshark` is the plain text group name
- `x` stands for the group password, which is typically not used in *Linux*
- `120` is the group ID `GID`
- `kali` and `root` are users that belong to this group. 

### Miscellanious <a id="whoami"></a>

The `whoami` command prints the current user you are logged in as. 

```
┌──(root💀kali)-[~]
└─# whoami
root
```

