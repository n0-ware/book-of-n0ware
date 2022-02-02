# reg
###### Tags[^1]
The `reg` command is used to interact with the [Windows Registry](../../../../book-of-n0ware/Knowledge%20Base/Concepts/Windows/Windows%20Registry.md)
## Syntax
```
C:\>reg /?

REG Operation [Parameter List]

  Operation  [ QUERY   | ADD    | DELETE  | COPY    |
               SAVE    | LOAD   | UNLOAD  | RESTORE |
               COMPARE | EXPORT | IMPORT  | FLAGS ]

Return Code: (Except for REG COMPARE)

  0 - Successful
  1 - Failed

For help on a specific operation type:

  REG Operation /?

Examples:

  REG QUERY /?
  REG ADD /?
  REG DELETE /?
  REG COPY /?
  REG SAVE /?
  REG RESTORE /?
  REG LOAD /?
  REG UNLOAD /?
  REG COMPARE /?
  REG EXPORT /?
  REG IMPORT /?
  REG FLAGS /?
```

**Common Arguments**
- `query` &mdash; Used to query the registry
- `delete` &mdash; Used to delete a set of registry keys
	- `-va` will delete all the values under a key
	- `-ve` will delete the value of an empty value name
	- `-v [ValueName]` specifies a value to delete by name
- `add` &mdash; Specify values to add to a key
## Examples
A common use of the `reg` command is to `QUERY` various registry key values. 

```
C:\>reg query hkcu

HKEY_CURRENT_USER
    P_Margin_Top    REG_DWORD    0x3e8
    P_Margin_Left    REG_DWORD    0x3e8
    P_Margin_Bottom    REG_DWORD    0x3e8
    P_Margin_Right    REG_DWORD    0x3e8

HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\SOFTWARE
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\Volatile Environment
```

From here, we can navigate inward, following the path of other keys, to the value we want. Lets dive into the keys in `Software` as far as we can go until we find the current `tenants` of `OneDrive`. 

```
C:\>reg query hkcu\Software\Microsoft\OneDrive\Accounts\Personal\Tenants\OneDrive

HKEY_CURRENT_USER\Software\Microsoft\OneDrive\Accounts\Personal\Tenants\OneDrive
    C:\Users\n0_ware\OneDrive    REG_DWORD    0x1aab
```

Another example is to see the software that is designed to run on system startup. You will likely recognize many of these files as familiar programs that start on system boot. 

```
C:\>reg query hkcu\software\microsoft\windows\currentversion\run

HKEY_CURRENT_USER\software\microsoft\windows\currentversion\run
    Discord    REG_SZ    C:\Users\n0_ware\AppData\Local\Discord\Update.exe --processStart Discord.exe
    Adobe Acrobat Synchronizer    REG_SZ    "C:\Program Files (x86)\Adobe\Acrobat DC\Acrobat\AdobeCollabSync.exe"
    Steam    REG_SZ    "C:\Program Files (x86)\Steam\steam.exe" -silent
    OneDrive    REG_SZ    "C:\Program Files\Microsoft OneDrive\OneDrive.exe" /background
    GoogleDriveFS    REG_SZ    "C:\Program Files\Google\Drive File Stream\54.0.3.0\GoogleDriveFS.exe" --startup_mode
    Adobe Reader Synchronizer    REG_SZ    "C:\Program Files (x86)\Adobe\Acrobat Reader DC\Reader\AdobeCollabSync.exe"
    org.openvpn.client    REG_SZ    C:\Program Files\OpenVPN Connect\OpenVPNConnect.exe --opened-at-login --minimize
    com.squirrel.slack.slack    REG_SZ    "C:\Users\n0_ware\AppData\Local\slack\slack.exe" --process-start-args --startup
```

 The relationship between the first and second set of queried keys is that on startup, *OneDrive* will run, and the keys under `...Tenants\OneDrive` inform which accounts are currently a `tenant` of the application. 

### Adding
It is simple to add keys to the registry, though the values themselves are complex in what they accomplish. Here is an example of a nonsense value in the registry. 

```
C:\>reg add hkcu\environment /v MyRegValue /t REG_NONE /d "Adding registry keys is just this easy"
The operation completed successfully.

    MyRegValue    REG_NONE    41006400640069006E00670020007200650067006900730074007200790020006B0065007900730020006900730020006A0075007300740020007400680069007300200065006100730079000000
```

Decoded from `hex`, the value is
```
A.d.d.i.n.g. .r.e.g.i.s.t.r.y. .k.e.y.s. .i.s. .j.u.s.t. .t.h.i.s. .e.a.s.y...
```
 ### Export-Import
 To export a portion of the registry to file, we use the `export` subcommand. These files can be used as a backup, or imported into another computer as a configuration baseline or for other purposes. 

```
C:\>reg export hkcu\software\microsoft\windows\currentversion\run reg_export
The operation completed successfully.

C:\>dir reg_export
 Volume in drive C is Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\

01/30/2022  12:17 AM             1,820 reg_export
               1 File(s)          1,820 bytes
               0 Dir(s)  165,578,444,800 bytes free

C:\>type reg_export
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\software\microsoft\windows\currentversion\run]
"Discord"="C:\\Users\\n0_ware\\AppData\\Local\\Discord\\Update.exe --processStart Discord.exe"
"Adobe Acrobat Synchronizer"="\"C:\\Program Files (x86)\\Adobe\\Acrobat DC\\Acrobat\\AdobeCollabSync.exe\""
"Steam"="\"C:\\Program Files (x86)\\Steam\\steam.exe\" -silent"
"OneDrive"="\"C:\\Program Files\\Microsoft OneDrive\\OneDrive.exe\" /background"
"GoogleDriveFS"="\"C:\\Program Files\\Google\\Drive File Stream\\54.0.3.0\\GoogleDriveFS.exe\" --startup_mode"
"Adobe Reader Synchronizer"="\"C:\\Program Files (x86)\\Adobe\\Acrobat Reader DC\\Reader\\AdobeCollabSync.exe\""
"org.openvpn.client"="C:\\Program Files\\OpenVPN Connect\\OpenVPNConnect.exe --opened-at-login --minimize"
"com.squirrel.slack.slack"="\"C:\\Users\\n0_ware\\AppData\\Local\\slack\\slack.exe\" --process-start-args --startup"
```

As an example attack path, consider this export. 

```
C:\>reg export hkcu\Environment reg_export_environment
The operation completed successfully.

C:\>type reg_export_environment
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Environment]
"OneDrive"=hex(2):43,2e,3a,2e,5c,2e,55,2e,73,2e,65,2e,\
72,2e,73,2e,5c,6e,2e,30,2e,5f,2e,77,2e,61,2e,72,2e,65,\
2e,5c,2e,4f,2e,6e,2e,65,2e,44,2e,72,2e,69,2e,76,2e,65,2e,2e,2e
```

Converting the exported value from `hex` to actual text reveals a specific value.

```
C.:.\.U.s.e.r.s.\n.0._.w.a.r.e.\.O.n.e.D.r.i.v.e...
```

Imagine if this was something sensitive, and we were able to extract this from the registry. The lesson is, **keep the registry secure**

A registry key can be imported via the `reg import` subcommand. 
 [^1]: #windows #fundamental 
