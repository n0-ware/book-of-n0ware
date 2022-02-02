# fdisk

The `fdisk` command is a tool used to create and manipulate partition tables on a *Linux* [Filesystem](../../../Knowledge%20Base/Linux%20Fundamentals/16%20Managing%20Memory%20and%20Disk.md#Filesystem). When attempting to [mount](mount.md) a new device, such as an external hard drive, `fdisk` can be used to get information on the new device, such as type and size, before mounting it. 

## Syntax
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

If we wanted to, we could then [mount](mount.md) this device to our system. 