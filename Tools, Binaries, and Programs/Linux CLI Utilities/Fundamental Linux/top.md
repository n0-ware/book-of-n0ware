# top
## Description

The `top` command is used to view a dynamic, real-time list of running *Linux* by the resources used. View the [man](https://man7.org/linux/man-pages/man1/top.1.html) page for more detailed information on using `top`. 

Holding <kbd>shift</kbd>+<kbd>f</kbd> will bring up an interactive menu you can use to sort with the Up and Down arrows.

```
Fields Management for window 1:Def, whose current sort field is %MEM
   Navigate with Up/Dn, Right selects for move then <Enter> or Left commits,
   'd' or <Space> toggles display, 's' sets sort.  Use 'q' or <Esc> to end!

* PID     = Process Id             SUPGIDS = Supp Groups IDs     
* USER    = Effective User Name    SUPGRPS = Supp Groups Names   
* PR      = Priority               TGID    = Thread Group Id     
* NI      = Nice Value             OOMa    = OOMEM Adjustment    
* VIRT    = Virtual Image (KiB)    OOMs    = OOMEM Score current 
* RES     = Resident Size (KiB)    ENVIRON = Environment vars    
* SHR     = Shared Memory (KiB)    vMj     = Major Faults delta  
* S       = Process Status         vMn     = Minor Faults delta  
* %CPU    = CPU Usage              USED    = Res+Swap Size (KiB) 
* %MEM    = Memory Usage (RES)     nsIPC   = IPC namespace Inode 
* TIME+   = CPU Time, hundredths   nsMNT   = MNT namespace Inode 
* COMMAND = Command Name/Line      nsNET   = NET namespace Inode 
  PPID    = Parent Process pid     nsPID   = PID namespace Inode 
  UID     = Effective User Id      nsUSER  = USER namespace Inode
  RUID    = Real User Id           nsUTS   = UTS namespace Inode 
  RUSER   = Real User Name         LXC     = LXC container name  
  SUID    = Saved User Id          RSan    = RES Anonymous (KiB) 
  SUSER   = Saved User Name        RSfd    = RES File-based (KiB)
  GID     = Group Id               RSlk    = RES Locked (KiB)    
  GROUP   = Group Name             RSsh    = RES Shared (KiB)    
  PGRP    = Process Group Id       CGNAME  = Control Group name  
  TTY     = Controlling Tty        NU      = Last Used NUMA node 
  TPGID   = Tty Process Grp Id  
  SID     = Session Id          
  nTH     = Number of Threads   
  P       = Last Used Cpu (SMP) 
  TIME    = CPU Time            
  SWAP    = Swapped Size (KiB)  
  CODE    = Code Size (KiB)     
  DATA    = Data+Stack (KiB)    
  nMaj    = Major Page Faults   
  nMin    = Minor Page Faults   
  nDRT    = Dirty Pages Count   
  WCHAN   = Sleeping in Function
  Flags   = Task Flags <sched.h>
  CGROUPS = Control Groups      
```
