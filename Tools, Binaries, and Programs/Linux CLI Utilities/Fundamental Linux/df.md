# Disk Free (df)

## Syntax

The [df](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20(Not%20Spellchecked)/df.md) command stands for `disk free` and will output information on the various disk(s) currently in use. 

```
┌──(root💀kali)-[/home/kali/Documents/GitHub/book-of-n0ware]
└─# df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             3004864         0   3004864   0% /dev
tmpfs             609504      1004    608500   1% /run
/dev/sda1       81000912  19787752  57052548  26% /
tmpfs            3047520     36416   3011104   2% /dev/shm
tmpfs               5120         0      5120   0% /run/lock
tmpfs             609504        64    609440   1% /run/user/1000
VM_Share       976797816 531562524 445235292  55% /media/sf_VM_Share
```

Here, you can even see the disk space, used space, and available space on the `VM_Share` disk, which represents a shared folder between my Virtual Machine and Host Machine. 

Adding the `-h` flag helps make this human-readable. 

```
┌──(kali㉿kali)-[~]
└─$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.9G     0  2.9G   0% /dev
tmpfs           596M 1016K  595M   1% /run
/dev/sda1        78G   19G   55G  26% /
tmpfs           3.0G     0  3.0G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           596M   60K  596M   1% /run/user/132
tmpfs           596M   64K  596M   1% /run/user/1000
```

Adding the `-T` option will show the type of filesystem on the devices listed. 

```
┌──(kali㉿kali)-[~]
└─$ df -T
Filesystem     Type     1K-blocks     Used Available Use% Mounted on
udev           devtmpfs   3004900        0   3004900   0% /dev
tmpfs          tmpfs       609504      972    608532   1% /run
/dev/sda1      ext4      81000912 17507588  59332712  23% /
tmpfs          tmpfs      3047520        0   3047520   0% /dev/shm
tmpfs          tmpfs         5120        0      5120   0% /run/lock
tmpfs          tmpfs       609504       64    609440   1% /run/user/1000
```

### dd


`dd` is a command-line utility with the primary purpose being to copy files, often large sections of files such as boot drives for backup. 

`dd` differs from `cp` in that it has options to control byte sizes, convert, and more. 

See [Geeks for Geeks](https://www.geeksforgeeks.org/dd-command-linux/) for an excellent demonstration of using `dd`.

### du

`du` is used to get information at a file-level on the disk. For example, running `du` in the "home" directory of a file system set to go traverse 3 directories. 

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

It can also be used to "summarize" the space a file takes on the system with the `-s` flag. 

```
┌──(kali㉿kali)-[~/Downloads]
└─$ du -hs   
2.0G    .
```

The `.` here denotes "here" as the location, meaning `Downloads` in this case. 

See [du](du.md) for file-level disk usage