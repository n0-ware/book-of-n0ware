# echo
###### Tags[^1]

The `echo` command is used to display messages to screen, such as the contents of an [Environment Variables](../../../Knowledge%20Base/Windows%20Fundamentals/05%20Windows%20Environment%20and%20System%20Information.md#Environment%20Variables). and to turn output messages from commands on or off. 

## Syntax
```
C:\>echo [options:] [file] # Basic Syntax 
C:\echo 2> NothingInside.txt #Creating a file. Similar to linux "tough"
C:\>echo "Sometext" > Somefile.txt # Adding text to a file
```

***Adding text to a file***
```
C:\Users\n0_ware>echo "Sometext" > SomeFile.txt

C:\Users\n0_ware>type SomeFile.txt
"Sometext"
```

***Creating an empty file***
Direct the "error output" to a file with `echo`. 
```
C:\Users\n0_ware\dir1>dir
 Volume in drive C is Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\Users\n0_ware\dir1

01/26/2022  08:39 AM    <DIR>          .
01/26/2022  08:39 AM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  165,923,700,736 bytes free

C:\Users\n0_ware\dir1>echo 2> file1.txt
ECHO is on.

C:\Users\n0_ware\dir1>dir
 Volume in drive C is Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\Users\n0_ware\dir1

01/26/2022  08:39 AM    <DIR>          .
01/26/2022  08:39 AM    <DIR>          ..
01/26/2022  08:39 AM                 0 file1.txt
               1 File(s)              0 bytes
               2 Dir(s)  165,923,700,736 bytes free
```


 [^1]: #windows #fundamental 

 