# Windows Processes
###### Tags[^1] 
### Processes Explained
In windows, every program that runs is considered a *process*. From the Windows documentation. 

> Each _process_ provides the resources needed to execute a program. A process has a virtual address space, executable code, open handles to system objects, a security context, a unique process identifier, environment variables, a priority class, minimum and maximum working set sizes, and at least one thread of execution. Each process is started with a single thread, often called the _primary thread_, but can create additional threads from any of its threads.[^2]

That seems like a lot, but unpacking it is not hard. 
- A *process* acts like an environment. It is not the program alone, but the entire collection of resources, references, variables, and permissions required to run the program. Think of it as like a box that contains all the ingredients, instructions, and tools to make a recipe. 
- The process is assigned somewhere to run, the "virtual address space." 
- A process may call on system objects throughout the execution
- It is identified by a unique number, any child will have its number as a parent, and it will have the number of its a parent if that applies. These are the **PID** and the **PPID** for process and parent-process ID, respectively. 
- Handles are an abstract reference to a resource, such as memory or an open file. 
- Working sets refer to the collection of pages inside a *processes* virtual address space that was recently referenced, such as instructions the application executes. The size of the working set impacts memory.[^3]
- It runs under a security context, referencing a [Security Identifier](99%20Glossary%20(Windows).md#Security%20Identifiers%20SID) for the right permissions. 
- Finally, there is the code that is executing, using all the resources, and accomplishing a tax. 

What about *threads*?[^4] These are part of the process that is scheduled for execution. They share the processes resources and virtual address space. A process can have multiple threads, all happening at the same time or in a specific order. 

Microsoft's analogy for differentiating processes, threads, and programs themselves is excellent. If a process is a room, a thread is a person in a room. The program is the set of instructions that a person is supposed to follow, and that room contains the resources required or a way to get those resources, to accomplish the instructions. The threat is what is happening, the process is the room it is happening in, and the program is the eventual flow the thread drives. 

### Modes
An operating system can work in two different ways, methods, states, etc. when running a process. They are *Kernel Mode* and *User Mode*[^5]. Processes that are core to the operating system and need access to the underlying software are called operate in *Kernel mode*. Processes executed by the user run in *User Mode*. The computer switches modes quickly as needed and per processes.

The core difference is that in kernel mode, the underlying hardware is accessed, and these are short-lived and essential to the OS. User mode is where the majority of processes run, and where our interaction takes place. These processes do not have access to the underlying hardware. User-mode processes are where we will focus our attention, as well. Kernel mode is the realm of the developer, not our concern for fundamentals. 

### Inheritance
Much like the nature of inheriting [Windows Permissions](08%20Permissions%20with%20NTFS.md#Windows%20Permissions) from a parent folder, processes inherit information from their parents or give them to their children. From the process perspective, if *Process_A* creates *Process_B*, *Process_B* is the child of *Process_A*. The relationship between child and parent requires that both remain alive, and killing the instance of the parent will kill the instance of the child. The term "spawn" is applied to the act of one process creating or starting another. There are some exceptions to this, such as *smss.exe* spawning *winlogon.exe* and then shutting itself down. 

### Essential
If you have ever opened the task manager, you've seen the massive list of processes running in the background you never opened yourself. Many of these are essential to the operation of the system and are something you should never intentionally stop. Processes such as `explorer.exe` and `winlogon.exe` are examples. 

- **System** &mdash; The *System* process is an essential kernel-mode process that allows the OS to talk to the underlying hardware and is responsible for a myriad of additional child processes, each one crucial to User interaction and system functionality. It usually has the same PID, and on Windows 10, it is **4**. 
- **smss.exe** &mdash; This is the "session manager," responsible for maintaining the virtual address space and assigning it as needed. The *system* processes creates it twice. The first spawns *winlogon.exe* and *csrss.exe*. The first instance ends after it spawns the two processes, and a second one starts to act as a listener for if those two are stopped. If either is stopped, it tells *Windows* to crash or shut down. 
- **winlogon.exe** &mdash; Spawned by *smss.exe* and mainly responsible for authenticating users and loading profiles, the "Windows Logon" process also manages many other user-related functions after they are logged in. Ever used the task manager? Thank *winlogon.exe*. Because it is spawned by the first *smss.exe* that shuts down, it has no parent.
- **csrss.exe** &mdash; Spawned by *smss,exe*, the "Client Server Runtime Process" manages some background functions. If terminated, it will begin a system shutdown, and it is the eventual parent of *cmd.exe.*
- **explorer.exe** &mdash; Often confused with *iexplorer.exe*, which is "Internet Explorer," the "Windows Explorer" renders most of the Windows GUI interface. Shutting it down will render the user interface unusable. It has no parent, spawned by *userinit.exe* that shuts itself down afterward. The Start Menu, Task Bar, System Tray, and others. While shutting it down is not advised, if any GUI components break, restarting it via the "Task Manager" can help. It has several child processes. 
- **wininit.exe** &mdash; Named "Windows Startup," it starts a specific set of user-mode applications the system relies on for stability and core functionality. It has several children. It is started when a user logs in and must remain on for the duration of your session. One of the processes it starts is *lsass.exe*, the "Local Security Authority Subsystem Service," largely responsible for enforcing security policies on the system.

Read more about some of the crucial task manager processes [here](https://www.makeuseof.com/tag/vital-windows-task-manager-processes/)[^6]

## Management
### Listing
The equivalent process on Windows to the *Linux* [ps](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/ps.md) is [tasklist](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/tasklist.md). Used alone, it will simply list the running tasks, but there are available operators to filter and include more information. The `/FI filter` syntax allows us to filter by attributes, the simplest way to filter is by piping into [find](../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/find.md) with the string you expect to locate. One can filter be username, image name, service, PID, etc. 

```
C:\Users>tasklist /FI  "IMAGENAME eq firefox.exe"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
firefox.exe                  22864 Console                    1    303,036 K
firefox.exe                  19660 Console                    1     91,116 K
firefox.exe                  16888 Console                    1     93,736 K
firefox.exe                   7668 Console                    1    127,888 K
...

C:\Users>tasklist | find "firefox.exe"
firefox.exe                  22864 Console                    1    309,420 K
firefox.exe                  19660 Console                    1     90,116 K
firefox.exe                  16888 Console                    1     93,812 K
firefox.exe                   7668 Console                    1    127,944 K
...

```

View the [tasklist](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/tasklist.md) page to see more examples. 

An "enhanced" version of `tasklist` comes in the [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) suite of programs, named [pslist](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/pslist.md). The result is very similar, except that it is more powerful. For example, see how we can use `pslist` to list commands, filtered by "firefox", with a process-tree showing the parent and child processes. 

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

The command is far more powerful, allowing us to display threads, memory consumption, and more. 

To gain granular information regarding [Dynamic Link Libraries (DLL)](../Concepts/Windows/Dynamic%20Link%20Library%20(DLL).md), [listdlls](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/listdlls.md) command from [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md). A good choice for security professionals is to occasionally audit the "unsigned" DLLs, and we can use this tool to do so. 


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


### Ending
Process can be ended, or "killed," with the [taskkill](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/taskkill.md) command. The operation is very similar to [tasklist](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/tasklist.md), with the exception that it will end commands that any filters match. Above, we listed the `firefox.exe` command. 

```
C:\Users>tasklist /FI "IMAGENAME eq notepad.exe"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
notepad.exe                  23824 Console                    1     14,520 K

C:\Users>taskkill /PID 23824
SUCCESS: Sent termination signal to the process with PID 23824.

C:\Users>tasklist /FI "IMAGENAME eq notepad.exe"
INFO: No tasks are running that match the specified criteria.
```

Much like the `taskkill` command, [pskill](../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/pskill.md) is another [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) utility built to kill processes. 

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


## DLLs
The concept of "libraries" is universal to most programming languages. Essentially, a *library* is a set of code that accomplishes a specific task, enables a particular function, or otherwise "does something" that a programmer may want to incorporate into their code without having to write it themselves. It can be simple, or wildly complex, but in the end, programmers are able to pull in *libraries* to quickly and efficiently write code that builds on existing code to accomplish something else. 

In *Windows*, the libraries are known as [Dynamic Link Libraries (DLL)](../Concepts/Windows/Dynamic%20Link%20Library%20(DLL).md). They function together as a library of pre-written code that can be called upon by any number of applications at the same time to perform a task specific to the use case of the application calling on them. 

*Windows* uses an **enormous** amount of libraries at all times, and developers even use them to write code for *Windows*. 

*DLLs* are stored in specific files related to the [Directory Structure](04%20Directory%20Structure%20-%20Windows.md) of the particular architecture. In 64-bit versions, they live in **System32** and **SysWOW64**, containing 64 and 32-bit libraries, respectively. In 32-bit versions of *Windows*, all libraries are kept in **System32**. 

These are a common point of attack for malicious actors in a variety of ways. For example, in the event a DLL was deleted or otherwise not present, attackers can replace it with one of their own if they can put it where the application expects the missing one to be. The result can include privilege escalation, information disclosure, etc. 

A common list of *DLLs* can be found [here](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files) for further reading. 
[^1]: #windows #fundamental 
[^2]: https://docs.microsoft.com/en-us/windows/win32/procthread/about-processes-and-threads
[^3]: https://docs.microsoft.com/en-us/windows/win32/procthread/process-working-set#:~:text=The%20working%20set%20of%20a,DLLs%20and%20the%20system%20DLLs.
[^4]: https://www.geeksforgeeks.org/difference-between-process-and-thread/
[^5]: https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/overview-of-windows-components
[^6]: https://www.makeuseof.com/tag/vital-windows-task-manager-processes/