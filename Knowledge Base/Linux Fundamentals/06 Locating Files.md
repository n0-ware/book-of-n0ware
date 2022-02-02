# Locating Files

On the *Linux* file system, there are many ways to search for files. Three commands stand out as the most common and easy to use. They are

```
which
locate
find
```

## Table of Contents

- [which](#which)
- 

### which

The `which` command interacts with the `$PATH` variable to search for files that are in folders on the path. For exampe, below is the `$PATH` variable for my *Linux* machine. 

```
┌──(demouser㉿kali)-[~]
└─$ echo $PATH
/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/demohome/.dotnet/tools
```

Running the `which` command on a specific file name will return its [absolute](01%20Navigation.md#absolute) path if the file name can be found. 

```
┌──(demouser㉿kali)-[~]
└─$ which ping 
/usr/bin/ping
```

This is most often use to determine where a command is running from, or what version or specific binary is being used. 

### Locate

The fastest way to find the location of files or directories on *Linux* is the `locate` command. Locate runs so quickly because it searches a local database named `locate.db` instead of parsing through the entire hard disk each time. A regularly running task keeps this local database updated from time to time. 

For example, we can find the location of any "Metasploit" database files:

```
┌──(demouser㉿kali)-[~]
└─$ locate msfdb   
/etc/alternatives/msfdb
/usr/bin/msfdb
/usr/share/metasploit-framework/msfdb
/usr/share/metasploit-framework/lib/msfdb_helpers
/usr/share/metasploit-framework/lib/msfdb_helpers/db_interface.rb
/usr/share/metasploit-framework/lib/msfdb_helpers/pg_ctl.rb
/usr/share/metasploit-framework/lib/msfdb_helpers/pg_ctlcluster.rb
/usr/share/metasploit-framework/lib/msfdb_helpers/standalone.rb
/usr/share/metasploit-framework/tools/dev/msfdb_ws
/var/lib/dpkg/alternatives/msfdb
```

### find

The `find` command is much more extensive than `locate`. See [find](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/find.md) for more details. 