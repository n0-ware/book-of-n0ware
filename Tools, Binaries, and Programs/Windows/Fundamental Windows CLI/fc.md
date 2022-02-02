# fc
###### Tags[^1]
The `fc` command is useful for comparing two files
## Syntax
```
C:\>fc [drive1:][path1]filename1 [drive2:][path2]filename2
```

```
C:\Users\n0_ware\DemoDir>dir

 Directory of C:\Users\n0_ware\DemoDir

01/26/2022  08:54 AM    <DIR>          .
01/26/2022  08:54 AM    <DIR>          ..
01/26/2022  08:55 AM               103 CompareMeFirst.txt
               1 File(s)            103 bytes
               2 Dir(s)  165,911,601,152 bytes free

C:\Users\n0_ware\DemoDir>type CompareMeFirst.txt
"Navigating the Windows command line just takes some getting used to if you are familiar with Linux"

C:\Users\n0_ware\DemoDir>copy CompareMeFirst.txt CompareMeSecond.txt
        1 file(s) copied.

C:\Users\n0_ware\DemoDir>fc CompareMeFirst.txt CompareMeSecond.txt
Comparing files CompareMeFirst.txt and COMPAREMESECOND.TXT
FC: no differences encountered
```

 **Common Arguments**
 - `/C` &mdash; Disregard case of text 
 - `/B` &mdash; Perform a binary comparison 
 - `/L` &mdash; Compare 'ASCII' files
 - `/N` &mdash; Add line numbers to an 'ASCII' comparison 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental 
