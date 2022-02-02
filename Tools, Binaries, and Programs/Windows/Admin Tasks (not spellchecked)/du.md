# du
###### Tags[^1]
The `du` program is part of the [sysinternals](../Fundamental%20Windows%20CLI/sysinternals.md) suite of programs reports on disk usage. This is similar to the *Linux* [du](../../Linux%20CLI%20Utilities/Fundamental%20Linux/du.md) command. 
## Syntax
```
C:\>du

DU v1.62 - Directory disk usage reporter
Copyright (C) 2005-2018 Mark Russinovich
Sysinternals - www.sysinternals.com

usage: du [-c[t]] [-l <levels> | -n | -v] [-u] [-q] <directory>
   -c     Print output as CSV. Use -ct for tab delimiting.
          Use -nobanner to suppress banner.
   -l     Specify subdirectory depth of information (default is one level).
   -n     Do not recurse.
   -q     Quiet.
   -nobanner
          Do not display the startup banner and copyright message.
   -u     Count each instance of a hardlinked file.
   -v     Show size (in KB) of all subdirectories.

CSV output is formatted as:
Path,CurrentFileCount,CurrentFileSize,FileCount,DirectoryCount,DirectorySize,DirectorySizeOnDisk
```

## Examples
***Enumerating the disk usage in OneDrive directory 2 layers deep***
```
C:\>du -l 2 C:\Users\n0_ware\OneDrive\

DU v1.62 - Directory disk usage reporter
Copyright (C) 2005-2018 Mark Russinovich
Sysinternals - www.sysinternals.com

     189,612  c:\users\n0_ware\onedrive\Desktop\Photos
     194,557  c:\users\n0_ware\onedrive\Desktop
           0  c:\users\n0_ware\onedrive\Documents\Adobe
           0  c:\users\n0_ware\onedrive\Documents\Custom Office Templates
         734  c:\users\n0_ware\onedrive\Documents\Expungement
 105,686,382  c:\users\n0_ware\onedrive\Documents\InfoSec
           4  c:\users\n0_ware\onedrive\Documents\My Data Sources
     111,519  c:\users\n0_ware\onedrive\Documents\My Games
      42,006  c:\users\n0_ware\onedrive\Documents\OneNote Notebooks
   2,677,271  c:\users\n0_ware\onedrive\Documents\Pi-Related
           0  c:\users\n0_ware\onedrive\Documents\SQL Server Management Studio
           0  c:\users\n0_ware\onedrive\Documents\Visual Studio 2017
...
```
 **Common Arguments**
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental #sysinternals #ntfs 
