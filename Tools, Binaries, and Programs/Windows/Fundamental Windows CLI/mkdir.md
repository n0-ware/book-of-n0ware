# mkdir
###### Tags[^1]
The `mkdir` command is used to create a directory on the filesystem. 

## Syntax
```
C:\>mkdir dir1[\dir2\dir3\dir4]
```

The `mkdir` command interprets additional directories, after the first, as additional directories to create on the path. 

```
C:\Users\n0_ware\DemoDir>mkdir a\b\c\d # Creating an entire directory path at once

C:\Users\n0_ware\DemoDir>mkdir 1 2 3 4 # Creating multiple directories at once

C:\Users\n0_ware\DemoDir>dir

 Directory of C:\Users\n0_ware\DemoDir

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
01/26/2022  08:44 AM    <DIR>          1
01/26/2022  08:44 AM    <DIR>          2
01/26/2022  08:44 AM    <DIR>          3
01/26/2022  08:44 AM    <DIR>          4
01/26/2022  08:44 AM    <DIR>          a
               0 File(s)              0 bytes
               7 Dir(s)  165,919,735,808 bytes free

C:\Users\n0_ware\DemoDir>cd a

C:\Users\n0_ware\DemoDir\a>dir

 Directory of C:\Users\n0_ware\DemoDir\a

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
01/26/2022  08:44 AM    <DIR>          b
               0 File(s)              0 bytes
               3 Dir(s)  165,919,703,040 bytes free

C:\Users\Eddie\DemoDir\a>dir /S # Listing all of the subdirectories and contents of '\a'

 Directory of C:\Users\Eddie\DemoDir\a

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
01/26/2022  08:44 AM    <DIR>          b
               0 File(s)              0 bytes

 Directory of C:\Users\Eddie\DemoDir\a\b

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
01/26/2022  08:44 AM    <DIR>          c
               0 File(s)              0 bytes

 Directory of C:\Users\Eddie\DemoDir\a\b\c

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
01/26/2022  08:44 AM    <DIR>          d
               0 File(s)              0 bytes

 Directory of C:\Users\Eddie\DemoDir\a\b\c\d

01/26/2022  08:44 AM    <DIR>          .
01/26/2022  08:44 AM    <DIR>          ..
               0 File(s)              0 bytes
```
 [^1]: #windows #fundamental 

 