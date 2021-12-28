# TryHackMe - Advent of Cyber 2021 - Day 8
## Santa's Bag of Toys
> Edward Hartmann
> DATE

***<u>Refs/Links:</u>***
- [Advent of Cyber 2021 TOC](_AoC-2021_TOC.md)  
-  Tags[^1]
-  Flag[^2]

[^1]: #powershell #windows #logs #lolbas
[^2]: *Flag 1:* `Microsoft Windows 11 Pro`  
					*Flag 2:* `grinchstolechristmas`  
					*Flag 3:* `C:\Users\santa\AppData\Local\Microsoft\Windows\UsrClass.dat`  
					*Flag 4:* `certutil.exe`  
					

## Walkthrough

In this scenario, Santa's laptop has gone missing, and all we have access to are some [PowerShell](../../../tools_and_tricks/cli_utilities/powershell.md) transcription logs and an analysis machine. 

> Either start the attack box or login via your own VM through `RDP` using `xfreerdp` &mdash; `xfreerdp /u:Administrator /p:grinch123! /v:YOUR_IP_HERE`

## Question-1

Our first task is to identify the `OS Name` of Santa's laptop. This is the operating system. The first (earliest log file contains the answer &mdash; `PowerShell_transcript.LAPTOP._s3k_jad.20211128153510`. Someone ran the  `systeminfo`command on this PC. 

![OS Name](AoC-2021_Photos/Day_8/1.0_AoC-Day-8_12-27-21-OS-Name.png)

## Question-2

The second question asks us about the password set for a "backdoor" account and we are asked to parse through the logs to search for some suspicious activity. There are some indicators of questionable behavior via some of the commands ran in the logs. 

In the same log file as question 1, we see someone enumerated the user accounts on the laptop via the `net user` command. 

![net user Command](AoC-2021_Photos/Day_8/2.0_AoC-Day-8_12-27-21-net-user.png)

In the log, named `PowerShell_transcript.LAPTOP.k_dg27us.20211128153538`, we see the creation of a user account named `s4nta` with a long password, and that someone added this user as an `administrator`. 

![New Admin User s4nta](AoC-2021_Photos/Day_8/3.0_AoC-Day-8_12-27-21-Add-Backdoor-User.png)

If you scroll down further, you can see the actor confirmed this via the `wmic` command to check the `sid` or `security group identifier` field. 

## Question 3

In the third log file, `PowerShell_transcript.LAPTOP.Zw6PA+c4.20211128153734` we see evidence of someone copying some files as the backdoor user `s4nta`. First, they confirm they are logged in as the new user, navigate to the `Desktop` directory,  then copy a file named `UsrClass.day` from its home directory to the `Desktop`.

> Note: The portion of the `cd` command with `$env:USERPROFILE` is an "alias" or "variable" for the users current home environment, and for this user, that is `C:\Users\s4nta`.

![Copying a File](AoC-2021_Photos/Day_8/4.0_AoC-Day-8_12-27-21-Copying-a-File.png)

Note that the `.` after the file path basically says "my current location." The command esentially says `copy the_file_at_this_path HERE`. The actor confirms the successful copy with `dir -Force`, which displays all files in the directory. The first `dir` did not show the file. 

## Question 4

The next question asks us to identify something called a "Living off the Land" binary, which refers to native Windows binaries that exist on the system. These binaries are perfect for malicious actors as they are very unlikely, relatively speaking, to be flagged by endpoint detection software as they exist natively on the system. 

> You can read more about LOLbas at their GitHub page &mdash; [LOLbas Project](https://lolbas-project.github.io/)


</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>

[^1]: 
[^2]: 