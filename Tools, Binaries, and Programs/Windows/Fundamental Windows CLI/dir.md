# dir
###### Tags[^1]

The `dir` command lists the files in the current or specified directory. 

## Syntax

```
dir [options:] [path/filename]
```

Dir can be used to search for all files based on arguments or to search for specific files if `path/filename` is provided. Imagine a directory with a large number of files and you are looking for one specifically. 


## Examples

```
C:\Users\n0_ware\SearchMe>dir
 Volume in drive C is Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\Users\n0_ware\SearchMe

01/26/2022  09:57 AM    <DIR>          .
01/26/2022  09:57 AM    <DIR>          ..
01/26/2022  09:56 AM                14 file
01/26/2022  09:56 AM                14 file - Copy
01/26/2022  09:56 AM                14 file - Copy (10)
01/26/2022  09:56 AM                14 file - Copy (11)
...
01/26/2022  09:56 AM                14 file9 - Copy (7)
01/26/2022  09:56 AM                14 file9 - Copy (8)
01/26/2022  09:56 AM                14 file9 - Copy (9)
             144 File(s)          2,016 bytes
               2 Dir(s)  165,908,045,824 bytes free
```

There are `144` files here. How can we find one? By adding it to the `dir` command

```
C:\Users\n0_ware\SearchMe>dir foundme.txt


 Directory of C:\Users\n0_ware\SearchMe

01/26/2022  09:57 AM                14 foundme.txt
               1 File(s)             14 bytes
               0 Dir(s)  165,907,091,456 bytes free
```

What if it is hidden deep in a directory? We can use the `/S` flag to locate it, even with wildcards. 

```
C:\Users\n0_ware\SearchMe>dir /S found*

 Directory of C:\Users\n0_ware\SearchMe\1\2\3\4\5\6\7\8\9\10

01/26/2022  09:57 AM                14 foundme.txt
               1 File(s)             14 bytes

     Total Files Listed:
               1 File(s)             14 bytes
               0 Dir(s)  165,773,668,352 bytes free
```

## Listing Data Streams
The `/R` flag will list alternate data streams not visible with the standard `dir` command. 

```
 Directory of C:\Users

01/31/2022  09:07 AM    <DIR>          .
01/31/2022  09:07 AM    <DIR>          ..
01/31/2022  09:07 AM                 0 alternate_stream.txt
                                    48 alternate_stream.txt:ADS:$DATA
01/31/2022  09:04 AM                36 defeault_stream.txt
```

See [Data Streams](../../../Knowledge%20Base/Windows%20Fundamentals/12%20Data%20Streams.md) for information regarding how to use and read these alternate data streams. 

**Common Arguments**
- `/A` &mdash; List files based on attributes
	- `H` for hidden 
- `/D` &mdash; Wide display format with columns
- `/N` &mdash; New long-list format 
- `/O` &mdash; Specifies a sort order
- `/Q` &mdash; Lists the owner of the file
- `/S` &mdash; Displays the files and subdirectories


 [^1]: #windows #fundamental 

 