# pslist
###### Tags[^1]
The `pslist` command is an enhanced version of [tasklist](tasklist.md) capable of much more details output and filtering for local and remote process listing. 
## Syntax
```
C:\>C:\Program Files\SysinternalsSuite>pslist /?

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Usage: pslist [-d][-m][-x][-t][-s [n] [-r n] [\\computer [-u username][-p password][name|pid]
   -d          Show thread detail.
   -m          Show memory detail.
   -x          Show processes, memory information and threads.
   -t          Show process tree.
   -s [n]      Run in task-manager mode, for optional seconds specified.
               Press Escape to abort.
   -r n        Task-manager mode refresh rate in seconds (default is 1).
   \\computer  Specifies remote computer.
   -u          Optional user name for remote login.
   -p          Optional password for remote login. If you don't present
               on the command line pslist will prompt you for it if necessary.
   name        Show information about processes that begin with the name
               specified.
   -e          Exact match the process name.
   -nobanner   Do not display the startup banner and copyright message.
   pid         Show information about specified process.

All memory values are displayed in KB.
Abbreviation key:
   Pri         Priority
   Thd         Number of Threads
   Hnd         Number of Handles
   VM          Virtual Memory
   WS          Working Set
   Priv        Private Virtual Memory
   Priv Pk     Private Virtual Memory Peak
   Faults      Page Faults
   NonP        Non-Paged Pool
   Page        Paged Pool
   Cswtch      Context Switches
```


 **Common Arguments**
 - `-d` &mdash; Show information on the threads 
 - `-m` &mdash; Show deails on memory
 - `-t` &mdash; Show processes tree
 - `-x` &mdash; Show processes, memory, and thread detail
 - `-m` &mdash; Run in task manager mode 
 - `[name]` &mdash; Show information that begins with a specific name
 - `-e` &mdash; Exact match for a name

## Examples

***Basic Output**
```
C:\Program Files\SysinternalsSuite>pslist

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Process information for n0_puter:

Name                Pid Pri Thd  Hnd   Priv        CPU Time    Elapsed Time
Idle                  0   0  12    0     60   158:19:19.531    52:33:21.294
System                4   8 218 35686    204     0:32:48.875    52:33:21.294
Registry            148   8   4    0  12984     0:00:01.312    52:33:23.098
smss                572  11   2   53   1060     0:00:00.203    52:33:21.291
csrss               716  13  13  841   2220     0:00:03.156    52:33:17.363
wininit             836  13   1  162   1404     0:00:00.078    52:33:15.488
csrss               844  13  15  929   3772     0:01:30.250    52:33:15.485
services            908   9   8  814   6904     0:00:17.484    52:33:15.434
lsass               928   9  11 1644  11136     0:00:18.578    52:33:15.417
...
```

***Listing by Name with Memory, Threads, Processes***
```
C:\Program Files\SysinternalsSuite>pslist firefox -x

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Process and thread information for n0_puter:

Name                Pid      VM      WS    Priv Priv Pk   Faults   NonP Page
firefox           10480 4194303  229520  157984  270384   184373    101  987
 Tid Pri    Cswtch            State     User Time   Kernel Time   Elapsed Time
26980  10      9882     Wait:UserReq  0:00:00.953   0:00:00.515    0:01:43.912
17500   8       247     Wait:UserReq  0:00:00.000   0:00:00.031    0:01:43.839
19664   8         7       Wait:Queue  0:00:00.000   0:00:00.000      0:01:43.824
...
```
***Show Tree***
```
C:\Program Files\SysinternalsSuite>pslist firefox -t

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Process information for n0_puter:

Name                             Pid Pri Thd  Hnd      VM      WS    Priv
firefox                        10480   8  77 1498 4194303  228892  158836
  firefox                       4736   8  48  679 4194303   70284  229184
```
On this tree, you can see parent and child processes. The `firefox` process with **PID 10480** is the parent of the process **4736**. This can be confirmed with [wmic](wmic.md). 

```
C:\Users>wmic process where (processid=4736) get Caption,ParentProcessid
Caption      ParentProcessId
firefox.exe  10480
```

Conversely, we can view the children of the parent with a different [wmic](wmic.md) command. 
```
C:\Users>wmic process where (ParentProcessID=10480) get Caption,ProcessID
Caption      ProcessId
firefox.exe  4736
firefox.exe  13076
firefox.exe  5236
firefox.exe  25720
firefox.exe  9112
firefox.exe  12060
```
 [^1]: #windows #fundamental #sysinternals 
