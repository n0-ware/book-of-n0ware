# mount

The `mount` command is used to add filesystems to the single directory tree available on a *Linux* system

See [fdisk](fdisk.md) and [umount](umount.md) for related information. 
## Syntax

```
mount [options] [device] [mount_point]
```

Listing current `ext4` mounts on the filesystem. This is the main partition on this system. 

```
┌──(kali㉿kali)-[~]
└─$ mount -t ext4        
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
```

**Arguments**
- `-t` &mdash; Tells `mount` what type of filesystem you are mounting, such as `ext4` or lists the current types of filesystems currently mounted. 
- `--target` &mdash; Specify the target mount point explicitly
- `-l` &mdash; List current mounts

## Example

In combination with [fdisk](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20(Not%20Spellchecked)/fdisk.md), we can find the local location of a device to mount, the type of device we are mounting, then provide the type and location we want to mount the new device. 

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

file1.txt file2.txt file3.txt ....
```

This HDD is now mounted on the system and ready to use