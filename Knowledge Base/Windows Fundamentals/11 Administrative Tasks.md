# Administrative Tasks
###### Tags[^1] 
## Scheduling Tasks

Like on *Linux* with with [crontab](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/crontab.md), jobs can be scheduled on *Windows*[^2]. The tool used to for scheduling tasks on *Windows* is [schtasks](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/schtasks.md). 

Creating, listing, and running tasks is simple. For example, below we create a task that runs every day of the week at 5:30 PM starting the program *notepax.exe*. Following that, we can list it, then delete it, and verify it was deleted. 

```
C:\>schtasks /create /sc weekly /d * /tn takenotes /tr notepad.exe /st 23:13
SUCCESS: The scheduled task "takenotes" has successfully been created.

C:\>schtasks /query /tn takenotes

Folder: \
TaskName                                 Next Run Time          Status
======================================== ====================== ===============
takenotes                                1/30/2022 11:13:00 PM  Ready

C:\>schtasks /delete /tn takenotes
WARNING: Are you sure you want to remove the task "takenotes" (Y/N)? y
SUCCESS: The scheduled task "takenotes" was successfully deleted.

C:\>schtasks /query /tn takenotes
ERROR: The syste
```

To view the details of a specific tasks, you can query it by name using `/TN` and view the *XML* details with the `/XML` tag. 


There are incredible security implications for this command. With `schtasks`, we can define a user to run the command is. Throwing a reverse shell with `schtasks` is only too easy. If a user writes a binary file that, using `netcat`, creates a reverse shell for a remote attacker, running with administrative privileges via the `/RU` and `/RP` for user and password when creating the task, an attacker could easily obtain [Privilege Escalation (privsec)](../Vulnerabilities/Privilege%20Escalation%20(privsec).md) quickly and cleanly.

```
C:\>schtasks /query /tn takenotes /xml
<?xml version="1.0" encoding="UTF-16"?>
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task">
  <RegistrationInfo>
    <Date>2022-01-30T23:33:36</Date>
    <Author>N0_PUTER\n0_ware</Author>
    <URI>\takenotes</URI>
  </RegistrationInfo>
  <Principals>
    <Principal id="Author">
      <UserId>S-1-5-21-2184681898-1587991450-2606260337-1001</UserId>
      <LogonType>InteractiveToken</LogonType>
    </Principal>
  </Principals>
...

...
  </Triggers>
  <Actions Context="Author">
    <Exec>
      <Command>notepad.exe</Command>
    </Exec>
  </Actions>
</Task>
```

There is a lot of flexibility with [schtasks], see the manual page from *Microsoft* for more information, such as managing triggers such as `ONSTART` and `ONIDLE`, granular modifiers, and more.[^3]

## Managing the Disk
[Network File System (NFS)](../../../book-of-n0ware/Knowledge%20Base/Concepts/Network%20File%20System%20(NFS).md) is the primary file system all on *Windows* *NT* operating system families. Managing the filesystem can be done through both the GUI and the command line. From the command line perspective, there are several options for enumerating disk information, managing settings, etc. 

### fsutil
The [fsutil](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/fsutil.md) suite of programs is one such, enabling us to manage settings or gather information on connected filesystems. 

```
C:\>fsutil
---- Commands Supported ----

8dot3name         8dot3name management
behavior          Control file system behavior
dax               Dax volume management
dirty             Manage volume dirty bit
file              File specific commands
fsInfo            File system information
hardlink          Hardlink management
objectID          Object ID management
quota             Quota management
repair            Self healing management
reparsePoint      Reparse point management
storageReserve    Storage Reserve management
resource          Transactional Resource Manager management
sparse            Sparse file control
tiering           Storage tiering property management
transaction       Transaction management
usn               USN management
volume            Volume management
wim               Transparent wim hosting management
```

For example, we can list the volumes with the combination of `fsutil` and the subcommands `volume list`. 

```
C:\>fsutil volume list
Possible volumes and current mount points are:

\\?\Volume{0ce75045-2ec0-4c88-9e6f-ff9c0a3b2439}\
C:\

\\?\Volume{1f6a06e4-efc7-4ead-b0e6-06bf63ecd921}\

\\?\Volume{65093c95-c06e-4dd5-acb8-34b1460dfc7c}\
D:\

\\?\Volume{029b2a57-a77f-4f08-a3e0-34e31a0a0dd7}\
E:\

\\?\Volume{1b06e749-3dc5-4ce1-9294-d0ef7a5afae0}\
```

There is a wealth of possible configurations and commands using `fsutil`, and reviewing the documentation is necessary to gather the full perspective and use cases[^4].

### du
Much like the *Linux* [du](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/du.md) command that can inform us on disk usage, *Windows* has a [du](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/du.md) that comes with the [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) suite of programs. It is not a built in command, and it functions very similar to the *Linux* version, such as when listing the space occupied by a particular area of the filesystem and listed by a specified depth of directories. 

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
```


[^1]: #windows #fundamental 
[^2]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks
[^3]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-create
[^4]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil