# Registry Basics
###### Tags[^1] 
## Overview
On an operating system like *Windows*, configuration data is a very important information, often persistent, and accessed by a myriad of functions. *Windows* uses something called the **registry**[^2] as a database to store this configuration data for system components to store and retrieve this data. 

> It is important to note that the *Windows* registry is an attractive attack vector with a wide attack surface and ripe targets. Passwords and hashes can be extracted, crucial configurations changed, and essential functions tampered with if the proper permissions are not in place. 

The data contained in the registry varies according to the version of *Windows* in question. Applications use something called the "registry API" to retrieve, modify, or delete registry data. 

Modifying registry data should be done with care, never doing so with data you do not control and explicitly know the purpose for. Errors in the registry can break functions on the system, requiring you to restore the value to the state it was in prior to the errors. 

From a security perspective, it is **always** important to know the basics of configurations on a system, how they can be manipulated, and how they impact functionality of a system. In *Windows*, the registry contains *the most critical* system information, constantly used, referenced, and relied upon by the OS and applications during all phases of system operation. 

The registry contains both user and system information, and the ability to modify it can give anyone control over the applications and services running on the system, including if they run at all. Imagine being able to turn off or modify security protocols or change the paths to which core applications access data. This is the power of the registry. 

While the totality of the registry is outside of a brief demonstration, it remains important to understand it at a high-level. 

## Organization

The registry is organized by `hives` each one containing the basic unit of a  `keys` with a corresponding `values`. The registry is designed in a hierarchical structure, meaning keys can have sub-keys and related directories, but the basic data structure is a `key:value` pair. 

The `values` themselves have associated metadata &mdash; name, data type, and data content.[^3]

### Hives 
Changes can be made according to a hive, a set of keys and their values, such as for a user via the `HKEY_CURRENT_USER` hive or on the entire system via the `HKEY_LOCAL_MACHINE` hive. Every "hive" has predefined circumstances upon which the files associated with it are loaded into memory. This can be anything, from the launch of a specific program, the logon of a specific user, or system boot. 

The two keys above represent the concept of a *predefined key*[^4]. These keys act as doors to other keys on the system, creating a layer between open keys and also providing a way for applications to navigate the registry and manage entire categories of data. 

These *predefined keys* start, and will always stay, open. If something wants to write data to the registry, they must tell one of these already open keys which key they want to write to. Some of the most common *predeinfed keys* can be found [here](https://docs.microsoft.com/en-us/windows/win32/sysinfo/predefined-keys) for further reading, but a shortlist is below:

- **HKEY_USERS** &mdash; Related to user configuration, such as default and current user configurations
- **HKEY_LOCAL_MACHINE** &mdash; Defines the physical state of the computer, including hardware, networking devices, drivers, software, etc. 
- **HKEY_CURRENT_USER_LOCAL_SETTINGS** &mdash;  Defines the preferences of the current local user.
- **HKEY_CURRENT_USER (HKCU)** &mdash; Defines preferences and configurations of the current user. These keys and values will differ depending on the current user that is logged in, including non-user accounts. 
- **HKEY_CURRENT_CONFIG (HKCC)** &mdash; Related ot the hardware file of the local system. The crucial information here is the values contain only the differences between the **current** hardware configuration and the **standard** hardware configuration. Standard information is in the **HKEY_LOCAL_MACHINE** key.
- **HKEY_CLASSES_ROOT (HKCR)** &mdash; Defines file types of documents and the properties associated with them. Shell applications often use the keys located under this key. 

*Windows* has given us a table that lists some standard hives and supporting files. 

| REGISTRY HIVE | SUPPORTING FILES |
| :-: | :-: |
| **HKEY_CURRENT_CONFIG** |   
System, System.alt, System.log, System.sav | 
| **HKEY_CURRENT_USER** |   
Ntuser.dat, Ntuser.dat.log |
| **HKEY_LOCAL_MACHINE\\SAM** | Sam, Sam.log, Sam.sav |
| **HKEY_LOCAL_MACHINE\\Security** | Security, Security.log, Security.sav |
| **HKEY_LOCAL_MACHINE\\Software** | Software, Software.log, Software.sav |
| **HKEY_LOCAL_MACHINE\\System** | System, System.alt, System.log, System.sav |
| **HKEY_USERS\\.DEFAULT** |   
Default, Default.log, Default.sav |

### Using Keys
Registry keys have a indefinable number of uses cases, but we will use a common *Windows* example to illustrate using and accessing keys. *Windows* has the concept of `Run` and `RunOnce` keys that cause a program or programs to run when a user logs in[^5]. `Run` keys make a program run every time a user logs in, and `RunOnce` happen one time and then are deleted if the specified program successfully runs. They can be set for the user or the machine itself. 

> More of an advanced user topic, but useful in certain attack scenarios, the `RunOnce` keys may be prefixed with a `!` character that stops the key from being deleted until after the command successfully runs. Without this, the key will not cause a program to run until th next reboot. Adding a `*` prefix before a `RunOnce` key will cause the key to run even in Safe Mode. 

There are four default `Run` and `RunOnce` keys on a *Windows* system. 
-  **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run**
-  **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\RunOnce**
-  **HKEY_CURRENT_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Run**
-  **HKEY_CURRENT_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\RunOnce**

Editing, adding, or deleting keys can be done on the GUI or on the command line. The [Registry Editor](https://support.microsoft.com/en-us/topic/how-to-add-modify-or-delete-registry-subkeys-and-values-by-using-a-reg-file-9c7f37cf-a5e9-e1cd-c4fa-2a26218a1a23) it he GUI version and is opened with the `regedit` command.

On the command line, however, the [reg](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/reg.md) command is used to interact with the registry. There are a lot of ways to interact with the registry, but one of the more basic methods is to simply query the registry based on the open *predefined keys* and navigate inward. 

#### Query
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

You can add, delete, and modify keys. This is beyond the scope of this demonstration, and if you do choose to practice this, be sure to be careful and create backups of your registry before making changes.

### Syntax
The syntax of a registry key contains 11 possible values. One such is the `REG-SZ` value[^6], contained in the second column of output.

```
Discord    REG_SZ    C:\Users\n0_ware\AppData\Local\Discord\Update.exe --processStart Discord.exe
```

This indicates a string that should be considered as text. In this case, it is starting the update of `Discord` and starting the service itself. There is an entire potential list of values in a registry key, such as `REG_BINARY` for binary data, and a list can be found [here](https://confluence.uconn.edu/ikb/desktop-support/windows-10-support/understanding-the-registry-on-windows#:~:text=Registry%20values%20are%20name%2Fdata,letter%20case%20is%20not%20significant.). 

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



[1^]: #windows #fundamental #registry #security 
[^2]: https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry
[^3]: https://docs.microsoft.com/en-us/windows/win32/shell/hkey-type
[^4]: https://docs.microsoft.com/en-us/windows/win32/sysinfo/predefined-keys
[^5]: https://docs.microsoft.com/en-us/windows/win32/setupapi/run-and-runonce-registry-keys
[^6]: https://confluence.uconn.edu/ikb/desktop-support/windows-10-support/understanding-the-registry-on-windows#:~:text=Registry%20values%20are%20name%2Fdata,letter%20case%20is%20not%20significant.