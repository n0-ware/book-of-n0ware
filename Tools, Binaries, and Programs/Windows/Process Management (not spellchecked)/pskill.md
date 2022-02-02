# pskill
###### Tags[^1]
Similar to `taskkill`, this is a [sysinternals](sysinternals.md) utility capable of terminating local and remote processes by a specific PID or name. 
## Syntax
```
C:\>pskill [-t] [\\computer [-u username [-p password]]] <process ID | name>
     -t    Kill the process and its descendants.
     -u    Specifies optional user name for login to
           remote computer.
     -p    Specifies optional password for user name. If you omit this
           you will be prompted to enter a hidden password.
     -nobanner Do not display the startup banner and copyright message.
```

 **Common Arguments**
 - `-t` &mdash; Kill the entire process tree from the PID named down.  

 ## Examples

```
C:\Users>pslist -e firefox

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Process information for n0_puter:

Name                Pid Pri Thd  Hnd   Priv        CPU Time    Elapsed Time
firefox           10480   8  69 1335 167308     0:00:08.125     0:41:20.303
firefox            4736   8  45  666 229372     0:00:00.953     0:41:20.175
firefox           13076   8  28  429  59916     0:00:01.093     0:41:19.614
firefox            5236   8  29  426  96864     0:00:00.953     0:41:19.428
firefox           25720   8  20  377  27872     0:00:00.078     0:41:18.615
firefox            9112   8  20  377  27804     0:00:00.093     0:41:18.598
firefox           12060   8  20  377  27752     0:00:00.093     0:41:18.534

C:\Users>pskill -t 10480

PsKill v1.16 - Terminates processes on local or remote systems
Copyright (C) 1999-2016  Mark Russinovich
Sysinternals - www.sysinternals.com

7 processes descended from and including 10480 killed.


C:\Users>pslist -e firefox

PsList v1.4 - Process information lister
Copyright (C) 2000-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

Process information for n0_puter:

process firefox was not found on n0_puter
```
 [^1]: #windows #fundamental #sysinternals 
