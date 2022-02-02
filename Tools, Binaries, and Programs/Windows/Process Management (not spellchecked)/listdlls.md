# listdlls
###### Tags[^1]
The `listdlls` is another [sysinternals](../Fundamental%20Windows%20CLI/sysinternals.md) utility for listing *DLLs* currently in use. The command will return an **enormous** amount of information, requiring that we use some elements of filtering to find the information we want. 
## Syntax
```
C:\Program Files\SysinternalsSuite>listdlls /?

Listdlls v3.2 - Listdlls
Copyright (C) 1997-2016 Mark Russinovich
Sysinternals

usage: listdlls [-r] [-v | -u] [processname|pid]
usage: listdlls [-r] [-v] [-d dllname]
  processname   Dump DLLs loaded by process (partial name accepted)
  pid           Dump DLLs associated with the specified process id
  dllname       Show only processes that have loaded the specified DLL.
  -r            Flag DLLs that relocated because they are not loaded at
                their base address.
  -u            Only list unsigned DLLs.
  -v            Show DLL version information.
```

## Examples

Listing with a filter for "firefox"
```
C:\Program Files\SysinternalsSuite>listdlls firefox

Listdlls v3.2 - Listdlls
Copyright (C) 1997-2016 Mark Russinovich
Sysinternals

------------------------------------------------------------------------------
firefox.exe pid: 24096
Command line: "C:\Program Files\Mozilla Firefox\firefox.exe"

Base                Size      Path
0x0000000033460000  0x9b000   C:\Program Files\Mozilla Firefox\firefox.exe
0x000000002c490000  0x1f5000  C:\Windows\SYSTEM32\ntdll.dll
0x000000002a500000  0xbe000   C:\Windows\System32\KERNEL32.dll
0x0000000029e00000  0x2c8000  C:\Windows\System32\KERNELBASE.dll
0x0000000029d00000  0x100000  C:\Windows\System32\ucrtbase.dll
0x0000000010ee0000  0xb3000   C:\Program Files\Mozilla Firefox\mozglue.dll
```

***Listing unsigned DLLs***
```
C:\Users\Program Files\SysinternalsSuite>listdlls -u
...
Base                Size      Path
0x00000000256a0000  0x22000   c:\program files\rdp wrapper\rdpwrap.dll
        Verified:       Unsigned
        Publisher:      Stas'M Corp.
        Description:    Terminal Services Wrapper Library
        Product:        RDP Host Support
        Version:        1.5.0.0
        File version:   1.5.0.0
        Create time:    Wed Dec 10 14:17:30 2014
...
```
 **Common Arguments**
 - `-u` &mdash; Listing only unsigned DLLs, helpful for security auditing.

 [^1]: #windows #fundamental #sysinternals 
