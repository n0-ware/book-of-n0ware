# The Windows Shells
###### Tags[^1] 

Much like *Linux*, *Windows* also provides a command-line for users to interact with. Unlike *Linux*, the standard command prompt in *Windows* is much more limited than the *Linux* counterpart. To counteract the limited command prompt, *Windows* has created an entire suite of administrative and management tools that work together with the command line to increase its functionality. While the classic command prompt is useful, can list files and directories, execute commands, and more, many of the higher-level functions require another tool. While these may run on the command line, they are not built-in. Some of these are [PowerShell](99%20Glossary%20(Windows).md#PowerShell), [Windows Command-Line Interface WMIC](#Windows%20Command-Line%20Interface%20WMIC), and others.. 
## cmd.exe

The basic command line in *Windows* is named `cmd.exe`. This shell has similar functionality to *Linux*, but is more limited in its access than the *Linux* command line is. Additionally, the entire program must be started with administrator access if you need it, rather than simply providing the [sudo](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/sudo.md) command as is done on *Linux*. 

Among the basic similarities is the ability to navigate through, list, and interact with files and directories. Programs may be started, scripts run, and so forth. Where on *Linux* scripts are referred to as [Shell Scripts](../Linux%20Fundamentals/99%20Glossary%20(Linux).md#Shell%20Scripts) and end with the extension `.sh` by convention, they are called *batch files* on Windows. 

## PowerShell
[PowerShell](../../Tools,%20Binaries,%20and%20Programs/Windows/PowerShell.md) is a step above `cmd.exe` in its functionality, a far step. From the *Microsoft* website we get a good description of PowerShell

> *"PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework. PowerShell runs on Windows, Linux, and macOS."*

Heavily used by system administrators, PowerShell is a suite of its own tools packed with functionality. It can interact with the system, return [.NET](99%20Glossary%20(Windows).md#NET%20Framework) objects using [cmdlets](99%20Glossary%20(Windows).md#cmdlet) in a pipeline of commands. It also interfaces with the [Component Object Model (COM)](99%20Glossary%20(Windows).md#Component%20Object%20Model%20(COM)) and [Windows Management Instrumentation (WMI)](99%20Glossary%20(Windows).md#Windows%20Management%20Instrumentation%20(WMI)), allowing administrators to perform local and remote tasks on systems. 

*PowerShell* can be started via the windows command line with the `powershell.exe` command or by searching for it in the *Windows* taskbar. 

## Windows Command-Line Interface (WMIC)
*WMIC* is a command-line interface for managing *WMI* or *Windows Management Instrumentation*. Compatible with scripting languages such as Visual Basic and [PowerShell](99%20Glossary%20(Windows).md#PowerShell), a user can manage the *Windows* system locally and remotely as well as share information between other management applications for a seamless *Windows* management experience. 

See [wmic](../../Tools,%20Binaries,%20and%20Programs/Windows/wmic.md) for some usage examples. 

## Sysinternals
To help with *Windows* management, the [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) suite of programs provides a robust package of programs, such as [psinfo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/psinfo.md) and [accesschk](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/accesschk.md) for aid in various administrative functions. This program must be downloaded and added to the system, it is not native to *Windows*. 


[^1]: #windows #fundamental 