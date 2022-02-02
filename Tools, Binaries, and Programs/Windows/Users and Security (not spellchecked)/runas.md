# Runas
###### Tags[^1]

The `runas` command is used to a assume the identify, access level, profile, etc. of another "subject" on a Windows system. While not as powerful or universal as [sudo](../../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) on *Linux*, it does allow us to temporarily elevate privileges for the span of a single command.

## Syntax
```
C:\>RUNAS [ [/noprofile | /profile] [/env] [/savecred | /netonly] ] /user:<UserName> program

C:\>RUNAS [ [/noprofile | /profile] [/env] [/savecred] ] /smartcard [/user:<UserName>] program

C:\>RUNAS /trustlevel:<TrustLevel> program
```

Run `runas` without any arguments to see the full syntax

## Examples
Execute a program.

```
C:\>runas /user:windows-01\n0_ware "cmd /c notepad.exe [path to file]" # Open notepad as a user to read files
C:\>runas /user:windows-01\n0_ware "cmd /c explorer" # Open explorer as a different user
```

Change permissions

```
C:\>runas /user:windows-01\n0_ware "cmd /c icacls C:\User\s0me_where\sensitivefile.txt /grant n0_ware:(F)
```

 **Common Arguments**
 - `/user` &mdash; `<UserName>` should be in form USER@DOMAIN or DOMAIN\\USER
 - `/trustlevel` &mdash; Must be one of the trust levels listed via `/showtrustlevels` 
 


 [^1]: #windows #fundamental 
