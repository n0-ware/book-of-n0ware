# Permissions with NTFS
###### Tags[^1]
Modern Windows systems use [New Technology File System](99%20Glossary%20(Windows).md#New%20Technology%20File%20System) or **NTFS** as the engine to manage the permissions for files and folders on the system. NTFS is a powerful and multi-functional file system that deals with more than just permissions.

Files and directories are treated differently in *Windows*, just as they are in *Linux*, though *Windows* has far more permissions, rather than relying on the granular combinations of read, write, and execute that *Linux* does. 

Learning how permissions work on any system is paramount to understanding how to defend, or subvert, a secure architecture. 

## Windows Permissions
*Windows* permissions, as mentioned above are far more granular that *Linux*. You can read more about permissions [here](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN). There are also [Special Permissions for Files and Folders](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN) that will not be covered below. A list can be found [here](99%20Glossary%20(Windows).md#Special) 

Some important notes to keep in mind regarding *Windows* file permissions:
- Read is the only permissions required for a user to run scripts. *Execute* is not required. 
- Read is required to access both a shortcut and its target. 
- Write permissions allow a user to modify **all** of the content in a file, meaning they can delete the contents, even if they cannot delete the file itself. 
- Giving a user full control to a folder gives them the right to delete the files inside of it, even if they did not have the necessary permissions on the files themselves. 
- **Inheritance** means that the children (files and subfolders) inside a parent folder will have the *exact same permissions as the parent*. This is default behavior. This is different than *explicit* permissions, which are assigned either when an object is created or by user action. 

### Types
#### Basic
Below are the types of basic *Windows* file and folder permissions. The type of permission is on the left, and the effect it has on folders and files from the perspective of the subject it is assigned to are on the right. 

| Permission | Folders | Files |  
| :- | :- | :- | 
| **Read (R)**  | Viewing and listing of files/subfolders | Viewing (accessing) file contents.|  
| **Write (W)** | Adding files and subfolders | Write to a file |  
| **Read and Execute (RX)** | View and list files and subfolders  as well as execute files. This can be inherited. | Allows both viewing and accessing of file contents  as well as execute |  
| **List Folder Contents (RX)**| Viewing and listing of files and subfolders as well as file execution.  Only inherited by subfolders | n/a |  
| **Modify (M)** | Allows for reading and writing of files and subfolders as well as  deletion of the folder | Allows reading, writing, and deletion of files |  
| **Full Control (F)** | Allows all privileges; reading, writing, changing, deleting  of files and subfolders| ALlows reading, writing, changing, and  deleting of files |  


###### Special
These are the special permissions. Pay special attention to `WDAC` as this allows changing of permissions and `WO` that changes the owner.    
-   **D** - Delete
-   **RC** - Read control (read permissions)
-   **WDAC** - Write DAC (change permissions)
-   **WO** - Write owner (take ownership)
-   **S** - Synchronize
-   **AS** - Access system security
-   **MA** - Maximum allowed
-   **GR** - Generic read
-   **GW** - Generic write
-   **GE** - Generic execute
-   **GA** - Generic all
-   **RD** - Read data/list directory
-   **WD** - Write data/add file
-   **AD** - Append data/add subdirectory
-   **REA** - Read extended attributes
-   **WEA** - Write extended attributes
-   **X** - Execute/traverse
-   **DC** - Delete child
-   **RA** - Read attributes
-   **WA** - Write attributes

Worth noting are the types of [Inheritance](99%20Glossary%20(Windows).md#Inheritance) permissions. 

| Flag | Meaning | Description | 
| :- | :- | :- |
| **(OI)** | Object Inherit | Objects in this container will inherit the ACE. Applies to directories only |
| **(CI)**| Container Inherit | Containers in the parent will inherit the ace. Applies to directories only | 
| **(IO)**| Inherit Only | ACE is applied to the the objects in the container, but not the container itself. Only applies to directories |
| **(NP)**| Do not propagate inherit | ACE is inherited by containers and objects in the parent, but is not recursive. Applies only to directories |
| **(I)**| Inherit | Ace inherited from the parent container |

A [Special](99%20Glossary%20(Windows).md#Special) permissions to note is the `WDAC` permission, which stands for *Write DAC*, which allows the user to change permissions. 

### Modify
Modifying permissions on the command prompt relies on the [icacls](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/icacls.md) command. Running it on a file or folder will list out the current permissions related to that file or folder. 

```
C:\Users\Eddie>icacls Do*
Documents NT AUTHORITY\SYSTEM:(I)(OI)(CI)(F)
          BUILTIN\Administrators:(I)(OI)(CI)(F)
          HARTPUTER\Eddie:(I)(OI)(CI)(F)

Downloads NT AUTHORITY\SYSTEM:(I)(OI)(CI)(F)
          BUILTIN\Administrators:(I)(OI)(CI)(F)
          HARTPUTER\Eddie:(I)(OI)(CI)(F)
```

Each set of characters warpped in `()` pertain to a particular permissions, such as `(F)`, which indicates full control. 

The `/grant` and `/deny` are two common uses of `icacls`, and as they look, they are used to add or remove permissions to a file or folder. 

```
C:\Users>icacls permfile.txt /grant n0_ware:(RX)
processed file: permfile.txt
Successfully processed 1 files; Failed processing 0 files

C:\Users>icacls permfile.txt
permfile.txt HARTPUTER\n0_ware:(RX)
             NT AUTHORITY\SYSTEM:(I)(F)
             BUILTIN\Administrators:(I)(F)
             BUILTIN\Users:(I)(RX)
             Everyone:(I)(RX)
```

Permissions can be added in many ways, such as to a user or group, to an [Security Identifier](99%20Glossary%20(Windows).md#Security%20Identifiers%20SID), and so forth. 
### accessch.exe
A part of the [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) suite, [accesschk](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/accesschk.md) is used to enumerate the various permissions a specific [Security Principle](99%20Glossary%20(Windows).md#Security%20Principles) has on the system. The use of this command is complex, but a simple way to to use it is to provide a security principle and path to check. 

```
C:\Program Files\SysinternalsSuite>accesschk.exe n0_ware C:\

Accesschk v6.14 - Reports effective permissions for securable objects
Copyright ⌐ 2006-2021 Mark Russinovich
Sysinternals - www.sysinternals.com

RW C:\$AV_ASW
RW C:\$Recycle.Bin
R  C:\$Windows.~WS
R  C:\$WinREAgent
RW C:\AMD
   C:\Config.Msi
R  C:\Documents and Settings
...
```

[^1]: #windows #fundamental #security 
[^2]: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN