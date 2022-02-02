# umount

If we want to remove a disk from the filesystem, we do so with [umount](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20(Not%20Spellchecked)/umount.md). This is a simple process, requiring that we simply point to the mount we want to remove. Note that you cannot be actively using the mount point or the system will report that the `target is busy`. Be sure to navigate out of that directory, close any files in use, and shut down any services interacting with the mount point. 

```
┌──(kali㉿kali)-[~]
└─$ umount /mnt/HDD

┌──(kali㉿kali)-[~]
└─$ ls -a /mnt
. ..
```

See [mount](mount.md) for information on mounting devices to the [Filesystem](../../../Knowledge%20Base/Linux%20Fundamentals/16%20Managing%20Memory%20and%20Disk.md#Filesystem). 