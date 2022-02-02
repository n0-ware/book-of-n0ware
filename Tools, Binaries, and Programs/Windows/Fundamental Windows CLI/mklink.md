# mklink
###### Tags[^1]
The `mklink` command is for creating "hard" and "soft" links symbolic links. These links reference files on the system in different ways. 
- A "hard" link is a real file that is duplicated as the source file changes and points to an exact spot on a hard drive
- A "soft" link is simply a pointer, not a file itself, that links to the original file, not a specific point on a hard drive.



## Syntax
```
C:\>mklink [options] Link Target
```

## Example

### softlink
```
C:\Users\n0_ware\LinkDir1>type softlinkfile.txt
"This is text in a soft link"

C:\Users\n0_ware\LinkDir1>mklink a_soft_link softlinkfile.txt
symbolic link created for a_soft_link <<===>> softlinkfile.txt

C:\Users\n0_ware\LinkDir1>type a_soft_link
"This is text in a soft link"

C:\Users\n0_ware\LinkDir1>dir

 Directory of C:\Users\n0_ware\LinkDir1

01/26/2022  09:35 AM    <DIR>          .
01/26/2022  09:35 AM    <DIR>          ..
01/26/2022  09:35 AM    <SYMLINK>      a_soft_link [softlinkfile.txt]
01/26/2022  09:34 AM                32 softlinkfile.txt
               2 File(s)             32 bytes
               2 Dir(s)  165,904,584,704 bytes free

C:\Users\n0_ware\LinkDir1>

C:\Users\n0_ware\LinkDir1>echo "Changing text in a soft link" > softlinkfile.txt

C:\Users\n0_ware\LinkDir1>type a_soft_link
"Changing text in a soft link"
```

### hardlink
```
C:\Users\n0_ware\LinkDir1>type hardlinkfile.txt
"I am text in a hard link"

C:\Users\n0_ware\LinkDir1>mklink /H a_hard_link hardlinkfile.txt
Hardlink created for a_hard_link <<===>> hardlinkfile.txt

C:\Users\n0_ware\LinkDir1>dir

 Directory of C:\Users\n0_ware\LinkDir1

01/26/2022  09:42 AM    <DIR>          .
01/26/2022  09:42 AM    <DIR>          ..
01/26/2022  09:41 AM                29 a_hard_link
01/26/2022  09:41 AM                29 hardlinkfile.txt
               3 File(s)             58 bytes
               2 Dir(s)  165,906,096,128 bytes free

C:\Users\n0_ware\LinkDir1>type hardlinkfile.txt
"I am text in a hard link"

C:\Users\n0_ware\LinkDir1>echo "Changing text in a hard link" > hardlinkfile.txt

C:\Users\n0_ware\LinkDir1>type a_hard_link
"Changing text in a hard link"
```

 **Common Arguments**
- `/D` &mdash; Changes the link to a directory link instead of the default file link 
- `/H` &mdash; Creates a hard link instead of a symbolic link 




 [^1]: #windows #fundamental 
