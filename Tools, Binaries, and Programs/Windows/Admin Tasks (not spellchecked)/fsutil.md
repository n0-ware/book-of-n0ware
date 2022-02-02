# fsutil
###### Tags[^1]
The `fsutil` command brings up a full set of program used to manage drives. It is related to the management of [Network File System (NFS)](../../../../book-of-n0ware/Knowledge%20Base/Concepts/Network%20File%20System%20(NFS).md).

Unlike many *Windows* commands, there is no `help` or `/?` command. Simply list the subcommand with no arguments and it will provide the available commands, i.e., `fsutil volume diskfree`

See the documentation for robust help with the program.[^2]
## Syntax
```
C:\>fsutil
---- Commands Supported ----

8dot3name         8dot3name management
behavior          Control file system behavior
dax               Dax volume management
dirty             Manage volume dirty bit
file              File specific commands
fsInfo            File system information
hardlink          Hardlink management
objectID          Object ID management
quota             Quota management
repair            Self healing management
reparsePoint      Reparse point management
storageReserve    Storage Reserve management
resource          Transactional Resource Manager management
sparse            Sparse file control
tiering           Storage tiering property management
transaction       Transaction management
usn               USN management
volume            Volume management
wim               Transparent wim hosting management
```

## Examples
***Checking the available and free bytes on a system***
```
C:\>fsutil volume diskfree C:
Total free bytes        : 164,371,357,696 (153.1 GB)
Total bytes             : 499,453,857,792 (465.2 GB)
Total quota free bytes  : 164,371,357,696 (153.1 GB)
```

***Listing connected drives and their details***
```
C:\>fsutil fsinfo drives

Drives: C:\ D:\ E:\

C:\>fsutil fsinfo drivetype E:
E: - Fixed Drive

C:\>fsutil fsinfo volumeinfo E:
Volume Name : External SSD
Volume Serial Number : 0x34dcb82c
Max Component Length : 255
File System Name : NTFS # <---- File system NTFS
Is ReadWrite
Not Thinly-Provisioned
Supports Case-sensitive filenames
Preserves Case of filenames
Supports Unicode in filenames
Preserves & Enforces ACL's
```


 [^1]: #windows #fundamental #ntfs #administrative
 [^2]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil
