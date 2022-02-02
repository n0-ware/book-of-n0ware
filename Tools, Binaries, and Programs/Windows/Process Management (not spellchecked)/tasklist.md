# tasklist
###### Tags[^1]
The `tasklist` command does what it sounds like, it lists tasks. 
## Syntax
```
C:\>tasklist [/S system [/U username [/P [password]]]]
         [/M [module] | /SVC | /V] [/FI filter] [/FO format] [/NH]

```

## Examples
***Used alone, it displays running tasks. ***
```
C:\Users>tasklist

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
System Idle Process              0 Services                   0          8 K
System                           4 Services                   0      3,124 K
Registry                       148 Services                   0     30,692 K
smss.exe                       572 Services                   0        300 K
csrss.exe                      716 Services                   0      2,328 K
wininit.exe                    836 Services                   0        384 K
csrss.exe                      844 Console                    1      3,780 K
services.exe                   908 Services                   0      6,356 K
lsass.exe                      928 Services                   0     12,616 K
...
```

***Filters can be used to display be PID, image name, service, user, etc. ***
```
C:\Users>tasklist /FI "PID eq 4"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
System                           4 Services                   0      3,124 K
```

```
C:\Users>tasklist /FI "USERNAME eq n0_ware"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
sihost.exe                    2156 Console                    1     24,552 K
svchost.exe                   3880 Console                    1     21,400 K
svchost.exe                   3932 Console                    1      3,032 K
svchost.exe                   5208 Console                    1     16,828 K
taskhostw.exe                 5400 Console                    1     13,328 K
ctfmon.exe                    5612 Console                    1     10,396 K
explorer.exe                  5640 Console                    1    ...
```

```
C:\Users>tasklist /FI  "IMAGENAME eq firefox.exe"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
firefox.exe                  22864 Console                    1    303,036 K
firefox.exe                  19660 Console                    1     91,116 K
firefox.exe                  16888 Console                    1     93,736 K
firefox.exe                   7668 Console                    1    127,888 K
```

***Filters can be combined***
```
C:\Users>tasklist /FI "USERNAME eq n0_ware" /FI "STATUS eq unknown" 

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
svchost.exe                   3880 Console                    1     21,356 K
svchost.exe                   3932 Console                    1      3,032 K
RuntimeBroker.exe             8544 Console                    1     19,412 K
conhost.exe                  11552 Console                    1      1,172 K
RuntimeBroker.exe             1828 Console                    1      6,024 K
...
```

***Get PPID process with [wmic](../wmic.md)***
`wmic process where (processid=PROCID_HERE) get parentprocessid`
```
C:\Users>wmic process where (processid=1732) get parentprocessid
ParentProcessId
1972
```

***Filter with Find***
A shortcut to filtering can be done by piping the output into [find](../../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/find.md) or [findstr](findstr.md)
```
C:\Users>tasklist | find "firefox.exe"
firefox.exe                  22864 Console                    1    309,420 K
firefox.exe                  19660 Console                    1     90,116 K
firefox.exe                  16888 Console                    1     93,812 K
firefox.exe                   7668 Console                    1    127,944 K
...
```
 **Common Arguments**
 - `/U` &mdash; Specifies the user context to run the command 
 - `/P` &mdash; Gives the password for the user context 
 - `/V` &mdash; Makes the output more verbose.  
 -  `/O` &mdash; Order by PID
 - `` &mdash;
 - `/FI filter` &mdash; Filters by criteria. See the `/?` page for available filters
	 - `PID` is a commonly used filter, as well as `Services` for "Service name" and `MODUELS` for DLL name
	 - Operators can be used with filters, such as `eq` and `ne` for equals and does not equal, as well as greater/less than operators and their counterparts. 
	 - Filters are wrapped in quotes, `"USERNAME eq n0_ware"` 
	
 [^1]: #windows #fundamental 
