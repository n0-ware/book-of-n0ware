# psinfo
###### Tags[^1]

The `psinfo` command is used to view specific information about the system, such as the *Kernel version*, *Product type*, and more on local or remote systems.  

> `psinfo` is part of the [Sysinternals](../../../Knowledge%20Base/Windows%20Fundamentals/99%20Glossary%20(Windows).md#Sysinternals) suite of tools available for *Windows*. 
## Syntax
```
C:\Program Files\SysinternalsSuite>PsInfo.exe [options] [\\computer[,computer[,..]]|@file [-u Username [-p Password]]]
```

***Example Output***
```
PsInfo v1.78 - Local and remote system information viewer
Copyright (C) 2001-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

System information for \\HARTPUTER:
Uptime:                    11 days 4 hours 42 minutes 9 seconds
Kernel version:            Windows 10 Home, Multiprocessor Free
Product type:              Professional
Product version:           6.3
Service pack:              0
Kernel build number:       19043
Registered organization:
Registered owner:          Eddie
IE version:                9.0000
System root:               C:\Windows
Processors:                12
Processor speed:           3.7 GHz
Processor type:            AMD Ryzen 5 3600X 6-Core Processor
Physical memory:           7032 MB
Video driver:              NVIDIA GeForce GTX 1650 SUPER
```

 **Common Arguments**
 - `-u` &mdash; Specifies an optional user name for login to a remote computer.
 - `-p` &mdash; Specifies password for user name.
 - `-h` &mdash; Show installed hotfixes.
 - `-s` &mdash; Show installed software.
 - `filter` &mdash; `Psinfo` will only show data for the field matching the filter. e.g. `psinfo service` lists only the service pack field.
 - `computer` &mdash; Direct `PsInfo` to perform the command on the remote computer or computers specified. If you omit the computer
               name `PsInfo` runs the command on the local system, and if you specify a wildcard (`\\*`), `PsInfo` runs the command on all computers in the current domain.
 - `@file` &mdash; Run `PsInfo` against computers listed in `file`. 


 [^1]: #windows #fundamental #sysinternals #security 