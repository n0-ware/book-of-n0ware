# set
###### Tags[^1]

The `set` command is used to display a list of the current [Environment Variables](../../../Knowledge%20Base/Windows%20Fundamentals/05%20Windows%20Environment%20and%20System%20Information.md#Environment%20Variables) on the system in a clean output line-by-line, or to temporarily set a new environment variable or change an existing one. You can print a specific environment variable to screen with [echo](echo.md)

See the [setx](setx.md) command to make permanent changes. 
## Syntax
```
C:\>set [variable=[string]]
```

Without a variable and string, `set` will simply list variables. By providing a new variable and string, you can declare a new environment variable.

***With no variable***
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
```

***To set a new variable***
```
C:\>set newvar=Windows_Power_User

C:\>echo %newvar%
Windows_Power_User

C:\>
```

 **Common Arguments**
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental 
