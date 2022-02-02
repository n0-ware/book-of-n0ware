# pssuspend
###### Tags[^1]
The [sysinternals](../Fundamental%20Windows%20CLI/sysinternals.md) utility `pssuspend` is used to either suspend or resume a process, locally or remotely. In a situation where you don't want a processes stopped or killed entirely, we can simply suspend it. 
## Syntax
```
C:\Program Files\SysinternalsSuite>pssuspend /?

PsSuspend v1.07 - Process Suspender
Copyright (C) 2001-2016 Mark Russinovich
Sysinternals

PsSuspend suspends or resumes processes on a local or remote NT system.

Usage: pssuspend [-r] [\\RemoteComputer [-u Username [-p Password]]] <process Id or name>
     -r    Resume.
     -u    Specifies optional user name for login to
           remote computer.
     -p    Specifies optional password for user name. If you omit this
           you will be prompted to enter a hidden password.
     -nobanner Do not display the startup banner and copyright message.
```

With no options, it will suspend the process, and providing`-r` will resume. 

```
C:\Program Files\SysinternalsSuite>pssuspend firefox.exe

PsSuspend v1.07 - Process Suspender
Copyright (C) 2001-2016 Mark Russinovich
Sysinternals

7 processes named firefox.exe suspended.


C:\Program Files\SysinternalsSuite>pssuspend -r firefox.exe

PsSuspend v1.07 - Process Suspender
Copyright (C) 2001-2016 Mark Russinovich
Sysinternals

7 processes named firefox.exe resumed.
```

 **Common Arguments**
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental 
