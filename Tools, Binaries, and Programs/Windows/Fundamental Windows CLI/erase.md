# erase
###### Tags[^1]
The `erase` command is used to delete one or more files. Related to [del](del.md)

## Syntax
```
C:\>erase [options:] [file] 
```

```
C:\Users\n0_ware\DemoDir>dir

 Directory of C:\Users\n0_ware\DemoDir

01/26/2022  08:50 AM    <DIR>          .
01/26/2022  08:50 AM    <DIR>          ..
01/26/2022  08:50 AM                 0 Fee
               1 File(s)              0 bytes
               2 Dir(s)  165,916,430,336 bytes free

C:\Users\n0_ware\DemoDir>copy Fee Fi
        1 file(s) copied.

C:\Users\n0_ware\DemoDir>copy Fi Fo
        1 file(s) copied.

C:\Users\n0_ware\DemoDir>copy Fo Fum
        1 file(s) copied.

C:\Users\n0_ware\DemoDir>dir

 Directory of C:\Users\n0_ware\DemoDir

01/26/2022  08:50 AM    <DIR>          .
01/26/2022  08:50 AM    <DIR>          ..
01/26/2022  08:50 AM                 0 Fee
01/26/2022  08:50 AM                 0 Fi
01/26/2022  08:50 AM                 0 Fo
01/26/2022  08:50 AM                 0 Fum
```
**Common Arguments**
- `/F` &mdash; Forces delete of read-only files 
- `/P` &mdash; Asks for a prompt before deleting 
- `/A` &mdash; Select files to delete based on attributes of the file 
	- `:H` for hidden files


 [^1]: #windows #fundamental 

 