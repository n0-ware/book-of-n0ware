# Disk Usage (du)
The `du` command can determine the size of files and directories, using `-hs` to make the output human readable. By default, it lists the disk usage of the current folder in a tree format. The `-hs` flags make this much easier to read. 

See this as default

```
┌──(kali㉿kali)-[~/Downloads]
└─$ du | head
12      ./zeek-4.0.4/man
20      ./zeek-4.0.4/scripts/zeekygen
8       ./zeek-4.0.4/scripts/site
16      ./zeek-4.0.4/scripts/base/frameworks/dpd
136     ./zeek-4.0.4/scripts/base/frameworks/files/magic
168     ./zeek-4.0.4/scripts/base/frameworks/files
28      ./zeek-4.0.4/scripts/base/frameworks/input/readers
52      ./zeek-4.0.4/scripts/base/frameworks/input
20      ./zeek-4.0.4/scripts/base/frameworks/tunnels
56      ./zeek-4.0.4/scripts/base/frameworks/netcontrol/plugins
```

And then with `-hs`

```
┌──(kali㉿kali)-[~/Downloads]
└─$ du -hs   
2.0G    .
```

The `-d` flag can be used to control the depth. 

```
┌──(kali㉿kali)-[~]
└─$ du -hd 3
38M     ./Documents/GitHub/book-of-n0ware
5.0M    ./Documents/GitHub/course-notes
36M     ./Documents/GitHub/n0-ware.github.io
79M     ./Documents/GitHub
7.9M    ./Documents/Python/myVenv
8.2M    ./Documents/Python
12K     ./Documents/othertest
87M     ./Documents
...
```
