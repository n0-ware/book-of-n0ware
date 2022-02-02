# Glossary (Windows)
###### Tags[^1] 
### Windows

#### .NET Framework 
<a id ="net-framework"></a>
The *.NET Framework* is a developer platform that consists of tools, programming languages, and libraries used to build many different types of applications. The *Framework* is the initial implementation, supporting websites, services, desktop apps, and more. *.NET* is a cross-platform implementation built to run websites, services, and console applications on *Windows, Linux, and Mac*. It was previously known as *.NET Core* and is open source on *GitHub* for all developers to use.[^2]

#### PowerShell
*Microsoft* defines it as as the following &mdash; *"PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework. PowerShell runs on Windows, Linux, and macOS."* Furthermore, it was built on top of the [.NET Framework](#NET%20Framework) and uses something called [cmdlets](#cmdlet) to run and manage all of the administrative tasks. 

See [PowerShell](../../Tools,%20Binaries,%20and%20Programs/Windows/PowerShell.md)

#### cmdlet
Cmdlets performs actions. Generally speaking, this is to return a [NET Framework](#NET%20Framework) object for another command in the pipeline of commands. Cmdlets are usually one in a chain of commands that form a "pipeline" in [PowerShell](#PowerShell)
[^3]

#### Component Object Model (COM)
<a id ="com"></a>
[^4]
#### Windows Management Instrumentation (WMI)
<a id="wmi"></a>
[^5] 

#### Windows Management Instrumentation Command-Line (WMIC)
<a id="wmic"></a>
[wmic](../../Tools,%20Binaries,%20and%20Programs/Windows/wmic.md)[^6]

#### Environment Variable
<a id="env-variable"></a>
> Wikipedia: An **environment variable** is a [dynamic-named](https://en.wikipedia.org/wiki/Name_resolution_(programming_languages) "Name resolution (programming languages)") [value](https://en.wikipedia.org/wiki/Value_(computer_science) "Value (computer science)") that can affect the way running [processes](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)") will behave on a computer. They are part of the environment in which a process runs. For example, a running process can query the value of the TEMP environment variable to discover a suitable location to store [temporary files](https://en.wikipedia.org/wiki/Temporary_file "Temporary file"), or the HOME or USERPROFILE variable to find the [directory structure](https://en.wikipedia.org/wiki/Directory_structure "Directory structure") owned by the user running the process.[^7]

#### Sysinternals

The `sysinternals` suite of tools help with administration and add to the command line environment native to *Windows*. It is not a built-in suite, and must be downloaded, and contains a wealth of tools for admins to use in their day-to-day tasks.[^8]

There are a huge number of programs included in `sysinternals`, and covering all of them is beyond the scope of a fundamentals course. One tool, however, is useful for security professionals, and it is named `psinfo`. 

The first time `sysinternals` is used, you must add the `/accepteula` flag to accept the "End User License Agreement."

#### Security Principles
<a id="sec-principle"></a>
Security principals are any entity that can be authenticated by the operating system, such as a user account, a computer account, or a thread or process that runs in the security context of a user or computer account, or the security groups for these accounts. Security principals have long been a foundation for controlling access to securable resources on Windows computers. Each security principal is represented in the operating system by a unique security identifier (SID).[^9]

#### Security Identifiers (SID)
<a id ="sid"></a>
SIDs[^10] are a unique value of a varying length that is used to identify a "trustee,"[^11]which is a user account, group account, or logon session that some trusted source put on the [Access Control List](../Glossary%20(Global).md#Access%20Control%20Lists) and is stored in a secure database. The SID is associated with a user when they logon and it serves as an "access token" for the user. The access token is created by the [Local System Authority](#Local%20System%20Authority). This token is a protected object that contains the SID and and any rights the user has. The SID (or the token) identifies the user in all interactions with *Windows* security for the purpose of authorization. Each SID is unique and applies to either a single user or group. [Access Control Entities](../Glossary%20(Global).md#Access%20Control%20Entities) are assigned SIDs. 

SIDs are an alpha-numeric code such as **S-1-1-0**, each `-` separating a "component" with a specific meaning and effect on the principle it is associated with. 

#### Local System Authority
The *Local System Authority*[^12] or *LSA* is a protected subsystem that authenticates and logs users onto the local system. LSA also maintains information about all aspects of local security on a system, collectively known as the *Local Security Policy* of the system.

#### User Access Control
Every application requiring access to the administrator access token will prompt the user for their consent, with the exception of parent and child process. If a parent has been given consent, the child will also have it, provided they have the same integrity level.[^13]

#### New Technology File System
*Windows* NFTS is the primary file system for the most recent versions of *Windows* and *Windows* server. It is a proprietary journaling file system developed by *Microsoft* and the default system used since the start of the *NT* family of *Windows* operating systems. It replaced *FAT32* and is supported on both *Linux* and *BSD*. 

NTFS provides a full set of features that includes security descriptors, encryption, disk quotas, metadata, and more features. It uses [Access Control](../Concepts/Web/Access%20Control.md) via [Access Control Lists](../Glossary%20(Global).md#Access%20Control%20Lists) to specify permissions[^14] on files and folders, designate groups and users to permit or deny access, and decide the access type.[^15] 

#### Inheritance
The concept that any files or folders created inside a parent folder will have the same permissions as the parent. 

#### Trustee
A *trustee* is a user or group account or logon session that an [Access Control Entry](../Glossary%20(Global).md#Access%20Control%20Entries) applies to. Every ACE on a system is on an [Access Control Lists](../Glossary%20(Global).md#Access%20Control%20Lists) and has a globally unique [Security Identifiers SID](99%20Glossary%20(Windows).md#Security%20Identifiers%20SID) applied to it that identifies it on a system.

#### Permissions
Get a full list of permissions [here](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN)
##### Basic
| Permission | Folders | Files |  
| :- | :- | :- | 
| **Read (R)**  | Viewing and listing of files/subfolders | Viewing (accessing) file contents.|  
| **Write (W)** | Adding files and subfolders | Write to a file |  
| **Read and Execute (RX)** | View and list files and subfolders  as well as execute files. This can be inherited. | Allows both viewing and accessing of file contents  as well as execute |  
| **List Folder Contents (RX)**| Viewing and listing of files and subfolders as well as file execution.  Only inherited by subfolders | n/a |  
| **Modify (M)** | Allows for reading and writing of files and subfolders as well as  deletion of the folder | Allows reading, writing, and deletion of files |  
| **Full Control (F)** | Allows all privileges; reading, writing, changing, deleting  of files and subfolders| Allows reading, writing, changing, and  deleting of files |

##### Special
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

##### [Inheritance](99%20Glossary%20(Windows).md#Inheritance)

| Flag | Meaning | Description | 
| :- | :- | :- |
| **(OI)** | Object Inherit | Objects in this container will inherit the ACE. Applies to directories only |
| **(CI)**| Container Inherit | Containers in the parent will inherit the ace. Applies to directories only | 
| **(IO)**| Inherit Only | ACE is applied to the the objects in the container, but not the container itself. Only applies to directories |
| **(NP)**| Do not propagate inherit | ACE is inherited by containers and objects in the parent, but is not recursive. Applies only to directories |
| **(I)**| Inherit | Ace inherited from the parent container |

###### References
[^1]: #windows #fundamental 
[^2]: https://dotnet.microsoft.com/en-us/learn/dotnet/what-is-dotnet-framework
[^3]: https://docs.microsoft.com/en-us/powershell/scripting/developer/cmdlet/cmdlet-overview?view=powershell-7.1
[^4]: https://en.wikipedia.org/wiki/Component_Object_Model
[^5]: https://en.wikipedia.org/wiki/Windows_Management_Instrumentation
[^6]: https://docs.microsoft.com/en-us/windows/win32/wmisdk/wmic
[^7]: https://en.wikipedia.org/wiki/Environment_variable
[^8]: https://docs.microsoft.com/en-us/sysinternals/
[^9]: https://docs.microsoft.com/en-us/windows/security/identity-protection/access-control/security-principals
[^10]: https://docs.microsoft.com/en-us/windows/win32/secauthz/security-identifiers
[^11]: https://docs.microsoft.com/en-us/windows/win32/secauthz/trustees
[^12]: https://docs.microsoft.com/en-us/windows/win32/secgloss/l-gly
[^13]: https://docs.microsoft.com/en-us/windows/security/identity-protection/user-account-control/how-user-account-control-works
[^14]: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/bb727008(v=technet.10)?redirectedfrom=MSDN
[^15]: https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview