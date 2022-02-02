# Managing Memory and Disk
On *Linux*, there are a number of useful tools for managing a disk or filesystem, its memory, space both used and free on disk and in memory, and so on. The most commonly used tools are:

- [Disk](#Disk)
	- [fdisk](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/fdisk.md)
	- [mount](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/mount.md)
	- [umount](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/umount.md)
	- [df](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/df.md)
	- [dd](#dd)
	- [du](#du)
- [Memory](#Memory)
	- [free](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/free.md)

## Filesystem

## Disk

On *Linux*, the filesystem is treated as a single entity, everything on this system represented by *files* and stemming from a single *root* drive, located at `/`. This has some impact on the way other devices, additional hard drives, and other filesystems are treated that differ from other operating systems like *Windows*. Primarily, because of this single-tree structure, we need to `mount` additional filesystems we want to use, from external hard drives to USB drives. 

*Mounting* a filesystem refers to creating a location on the disk that represents this new filesystem. This carries with it some flexibility in that we can theoretically mount a disk anywhere on the system. Systems like [Network File System (NFS)](../Concepts/Network%20File%20System%20(NFS).md) are managed by *mount points* in this way, where an entire filesystem, or a portion of one, can be *mounted* to a location on a *Linux* directory tree. 

Normally, devices are stored in the `/dev` directory, and this is a good place to look if you are trying to identify a device you want to "mount."

### fdisk

Using `fdisk -l` will inform us as to the current partition tables available on the device. 

```
┌──(kali㉿kali)-[~]
└─$ sudo fdisk -l       

Disk /dev/sda: 80 GiB, 85899345920 bytes, 167772160 sectors
Disk model: VBOX HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf0f6b9b0

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 165771263 165769216   79G 83 Linux
/dev/sda2       165773310 167770111   1996802  975M  5 Extended
/dev/sda5       165773312 167770111   1996800  975M 82 Linux swap / Solaris
```

Imagine if we just plugged in a second, 10GB external hard drive to our machine. Running `fisk -l` would return a second "Device" section looking something like below after the image above. 

```
┌──(kali㉿kali)-[~]
└─$ sudo fdisk -l       
...
Disk /dev/sdb: 100 GiB, 1027604480 bytes, 20070400 sectors
Disk model: External Hard Drive   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf0f6a19c06

Device     Boot     Start      End   Sectors  Size Id Type
/dev/sdb1  *         32   20070499 20070068   10GB 97 FAT32
```

Some things to note
- The location of the device is `/dev/sbd1`
- The size is 10GB
- The type is `FAT32`

We can use the [mount](#mount) command to add this device to our filesystem. 

### mount

Fortunately, *Linux* has a command [mount](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/mount.md) that we can add filesystems to our directory tree. 

Listing current `ext4` mounts on the filesystem. This is the main partition on this system. 

```
┌──(kali㉿kali)-[~]
└─$ mount -t ext4        
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
```

In combination with [fdisk](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/fdisk.md), we can find the local location of a device to mount, the type of device we are mounting, then provide the type and location we want to mount the new device. 

Referencing the next section, `fdisk`, imagine we have identified our 10GB external hard drive at the location `/dev/sbd1`. We want to mount this device to our system. Most often, we use the directory `/mnt` already present on the system. We will create a directory inside `/mnt` for our new HDD and mount this device to our system. 

```
┌──(kali㉿kali)-[~]
└─$ sudo mkdir /mnt/HDD

┌──(kali㉿kali)-[~]
└─$ sudo mount /dev/sbd1 /mnt/usb

┌──(kali㉿kali)-[~]
└─$ cd /mnt/HDD

┌──(kali㉿kali)-[~]
└─$ ls 

file1.txt file2.txt file3.txt ...
```

This HDD is now mounted on the system and ready to use. We can "unmount" this device with the [[#]]

### umount

If we want to remove a disk from the filesystem, we do so with [umount](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/umount.md). This is a simple process, requiring that we simply point to the mount we want to remove. Note that you cannot be actively using the mount point or the system will report that the `target is busy`. Be sure to navigate out of that directory, close any files in use, and shut down any services interacting with the mount point. 

```
┌──(kali㉿kali)-[~]
└─$ umount /mnt/HDD

┌──(kali㉿kali)-[~]
└─$ ls -a /mnt
. ..
```

### df

The [df](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/df.md) command stands for `disk free` and will output information on the various disk(s) currently in use. 

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

Here, you can even see the disk space, used space, and available space on the `VM_Share` disk, which represents a shared folder between my Virtual Machine and Host Machine. Adding the `-h` flag will output this information in a human-readable format. 

### dd

The [dd](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/df.md#dd) command is used to copy or "duplicate" disks with more granularity than `cp`. 

### du

The [du](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/du.md) command is used to inform on the space various sectors of the file system take up, from highly detailed, recursive searching, down to a more summarized version at a space on the filesystem.

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

## Memory

### free

The [free](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/free.md) command informs us about the space used and available in the system memory. Where [du](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/du.md) and [df](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/df.md) are related to space on disk for file storage, `free` relates to the system memory. 

`free` is particularly useful on systems with no *GUI* where other system monitors cannot be used, and where the level of granularity provided by `top` is not required. 

See below where `free` is used with `-m` to show *megabytes* of storage that is free. 

```
┌──(kali㉿kali)-[~]
└─$ free -m
               total        used        free      shared  buff/cache   available
Mem:            5952         512        4053           4        1385        5146
Swap:            974           0         974
```

