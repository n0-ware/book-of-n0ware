# chown
## Description

The `chown` command is used to manage the "owner" and "group" of a file. For details on permissions, see <a href="#owner-group">owners and groups</a> in [File Permissions](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md). 

> Note that if you change the owner of a directory, all files create *inside* that directory will be owned by the owner of the directory, *not* the creator of the file. 

The concepts [setuid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setuid) and [setgid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setgid) are related to this. 

## Syntax

```
chown [arguments] owner:group [file]
```

For example, changing the owner of the `permissionsfile.txt` file to `kali`.

```
┌──(root💀kali)-[/home/demohome]
└─# ls -l permissionsfile.txt 
-rw-r-xr-- 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
                  
┌──(root💀kali)-[/home/demohome]
└─# chown kali permissionsfile.txt 

┌──(root💀kali)-[~demouser]
└─# ls -l permissionsfile.txt     
-rw-r-xr-- 1 kali demouser 0 Jan 19 21:16 permissionsfile.txt
```

To change the group only, leave the first portion of the `owner:group` syntax empty, providing only the group:

```
┌──(root💀kali)-[~demouser]
└─# ls -l permissionsfile.txt     
-rw-r-xr-- 1 kali demouser 0 Jan 19 21:16 permissionsfile.txt
                                                                                     
┌──(root💀kali)-[~demouser]
└─# chown :kali permissionsfile.txt 
                                                                                     
┌──(root💀kali)-[~demouser]
└─# ls -l permissionsfile.txt 
-rw-r-xr-- 1 kali kali 0 Jan 19 21:16 permissionsfile.txt
```

To change both back to kali at the same time:

```
┌──(root💀kali)-[~demouser]
└─# ls -l permissionsfile.txt 
-rw-r-xr-- 1 kali kali 0 Jan 19 21:16 permissionsfile.txt
                  
┌──(root💀kali)-[~demouser]
└─# chown demouser:demouser permissionsfile.txt 
                 
┌──(root💀kali)-[~demouser]
└─# ls -l permissionsfile.txt
-rw-r-xr-- 1 demouser demouser 0 Jan 19 21:16 permissionsfile.txt
```

This can be done to a directory as well, and if you'd like the change to impact all the files inside that directory, use the recursive flag `-R`.

```
┌──(root💀kali)-[/home/kali]
└─# ls -l permissionsDir     
total 0
-rw-r--r-- 1 kali kali 0 Jan 19 21:46 file1.txt
-rw-r--r-- 1 kali kali 0 Jan 19 21:46 file2.txt
-rw-r--r-- 1 kali kali 0 Jan 19 21:46 file3.txt                                                                                
┌──(root💀kali)-[/home/kali]
└─# ls -l               
total 52
drwxr-xr-x 2 kali kali 4096 Jan 19 21:46 permissionsDir
                 
┌──(root💀kali)-[/home/kali]
└─# chown -r demouser:demouser permissionsDir  
chown: invalid option -- 'r'
Try 'chown --help' for more information.
                  
┌──(root💀kali)-[~kali]
└─# chown -R demouser:demouser permissionsDir                                                      
┌──(root💀kali)-[~kali]
└─# ls -l permissionsDir 
total 0
-rw-r--r-- 1 demouser demouser 0 Jan 19 21:46 file1.txt
-rw-r--r-- 1 demouser demouser 0 Jan 19 21:46 file2.txt
-rw-r--r-- 1 demouser demouser 0 Jan 19 21:46 file3.txt
```
