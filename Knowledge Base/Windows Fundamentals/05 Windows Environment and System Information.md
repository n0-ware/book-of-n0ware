# Windows Environment Variables and System Information
###### Tags[^1] 

Like any operating system, *Windows* environments have information valuable to the user, and certain static and dynamic environment variables, all of this available to the user via various built in and executable commands. 

## System Information
The [systeminfo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/systeminfo.md) command is used to pull out a granular list of details related to the system currently running or a remote machine if desired. Used with [findstr](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/findstr.md), this can be a quick info gathering tool. 

## Environment
### Environment Variables
On *Linux*, [Environment Variables](99%20Glossary%20(Windows).md#Environment%20Variable) are noted with a `$` before them. For example, the `$PATH` variable outputs the available paths for executable files. On *Windows*, however, environment variables are wrapped in `%` characters. For example, the `%username%` environment variable stores the username of the current user on *Windows* where `$USER` stores it on *Linux*. These variables are used in countless ways, from programs to bash scripts, to keep the system running smoothly. The permanent environment variables on the system are set and stored in the [Windows Registry](../Concepts/Windows/Windows%20Registry.md)[^2]

Also similar to *Linux*, we can use the [echo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/echo.md) command to print the contents of an environment variable to file. 

```
C:\>echo %username%
n0_ware
```

Managing environment variables is done with [set](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/set.md) and [setx](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/setx.md). The `set` command can declare a new variable or change an existing one temporarily, where `setx` does so permanently. Here is an example of setting a temporary variable:

```
C:\>set newvar=Windows_Power_User

C:\>echo %newvar%
Windows_Power_User

C:\>
```

Running `set` without any arguments will print a list of all the permanent environment variables on the system, such as the `PathExt` variable, which lists the extensions the system can execute. As wit anything, this can be changed. 

```
C:\>set
ALLUSERSPROFILE=C:\ProgramData
AMDRMPATH=C:\Program Files\AMD\RyzenMaster\
APPDATA=C:\Users\n0_ware\AppData\Roaming
CommonProgramFiles=C:\Program Files\Common Files
CommonProgramFiles(x86)=C:\Program Files (x86)\Common Files
CommonProgramW6432=C:\Program Files\Common Files
COMPUTERNAME=HARTPUTER
ComSpec=C:\Windows\system32\cmd.exe
DriverData=C:\Windows\System32\Drivers\DriverData
HOMEDRIVE=C:
HOMEPATH=\Users\n0_ware
LOCALAPPDATA=C:\Users\n0_ware\AppData\Local
...

C:\>echo %PathExt%
.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
```

Some of the most common variables stored on *Windows* are
- **PATH** &mdash; Like the *Linux* path, this is where the system will look for executable files. 
- **USERNAME** &mdash; Prints the current user that is logged in
- **TEMP or TMP** &mdash; Prints the default "temp" directories used for temporary storage
- **UESRPOFILE** &mdash; The location of the profile for the current user. 
- **OS** &mdash; Prints the OS of the system
- **HOMEPATH** &mdash; Prints the home path, `/Users/[USER]`
[^1]: #windows #fundamental 
[^2]: https://en.wikipedia.org/wiki/Windows_Registry

## System Information Gathering
The ability to gain information on the system is important for administrators, power users, defenders, and attackers, whether locally or on a remote system. There are many commands and tools available to this purpose, some more granular than others, such as [systeminfo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/systeminfo.md) and the [Sysinternals](99%20Glossary%20(Windows).md#Sysinternals) suite of administrator. The [environment](#Environment) itself discloses a wealth of information for those that know how to look for it, such as by enumerating [Environment Variables](#Environment%20Variables) with [set](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/set.md) and [echo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/echo.md).

Particularly useful for security personal or offensive practitioners is the [psinfo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/psinfo.md) utility built in to `sysinternals`. It will display information about the system through a variety of possible filters and options that detail patch information, OS versions, host, owner, and more. 

[^1]: #windows #fundamental #filesystem #environment