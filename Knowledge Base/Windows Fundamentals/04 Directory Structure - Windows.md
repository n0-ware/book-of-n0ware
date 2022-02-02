# Directory Structure - Windows
###### Tags[^1] 

While *Windows* does not have what users refer to as the `root`, drive, there is still a "root" of the drive, and that is the *drive letter*. Most often, `C:\` is the root of the main drive, and it has a standard structure common to most systems and contains relevant system files, configuration files, user data, programs, and so on. 

Each of the directories discussed here briefly contains a wealth of files beyond the scope of this lesson, but it will serve as a baseline. 

Listing the `C:\` drive of a standard windows PC, here is the output. 

```
C:\>dir
 Volume in drive C is WD-Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\

12/07/2019  03:14 AM    <DIR>          PerfLogs
12/17/2021  11:06 AM    <DIR>          Program Files
12/17/2021  11:05 AM    <DIR>          Program Files (x86)
11/26/2021  07:58 AM    <DIR>          ProgramData
12/01/2021  08:15 AM    <DIR>          Users
12/16/2021  11:32 PM    <DIR>          Windows
```
- `\PerfLogs` &mdash; Usually empty, this file may windows *Windows* performance logs. On a default configuration, it will be empty. 
- `\Program Files` &mdash;
	- **32-bit architecture** &mdash; All programs, both 16 and 32-bit, are installed here. On this architecture size, it is the only "Program Files" folder available
	- **64-bit architecture** &mdash; 64-bit programs are installed here
-   `\Program Files (x86)` &mdash; This file only appears on **64-bit installations**. All **16 and 32-bit programs** are installed here. 
- `\Program Data` &mdash; This file is hidden by default, and it is used to store program data that other programs expect to be there and that they need to run. Specifically, it holds program data that needs to be accessed regardless of the user account in the context to which that program is running. 
	- For example, a program may require information needed to operate DVD recorders connected to the computer, and because all users need them, the data is stored here. 
	- Also, Windows Defender stores virus definitions in `\ProgramData\Microsoft\Windows Defender`.
- `\Users` &mdash; If a user logs in even once, they will have a directory in this with their name.
	- `\Users\Public` &mdash; A `\Users` directory that can be accessed by all users to be used to share files locally or across the network with valid user accounts and remote permissions. 
- `\Users\[UserName\AppData` &mdash; A hidden directory in `\Users` for storing application data and settings for each user. Within this folder are three more
	- `\Roaming`  &mdash; Used for network-based logins for "roaming profiles" and the data will synchronize when the computer logs in.  
	- `\Local\Temp` &mdash; Used to hold temporary files, as operating systems often need temporary space. These files are usually deleted at startup or reboot. 
- `\Windows` &mdash; This is a large folder filled with tons of directories and files. It contains the OS installation itself and related installation files. There are three key folders in this folder related to [Dynamic Link Libraries (DLL)](../Concepts/Windows/Dynamic%20Link%20Library%20(DLL).md). 
	- `\System` &mdash; Stories 16-bit DLL's, usually empty on a 64-bit installation
	- `\System32` &mdash; Stores either 32 or 64-bit DLL's, depending on the edition of Windows
	- `\SysWOW64` &mdash; Only appears on 64-bit installations and contains 32-bit DLL's
	- When a program calls on a DLL, and it is not present in that program's folder, the program searches these files to try and find it. 
	- This can be a great opportunity for [Windows Privilege Escalation](../Vulnerabilities/Privilege%20Escalation%20(privsec).md#Windows)
	- 
[^1]: #windows #fundamental #filesystem #privsec 