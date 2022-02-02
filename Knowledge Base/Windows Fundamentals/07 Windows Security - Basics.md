# Windows Security
###### Tags[^1]
## Table of Contents
- [Architecture](#Architecture)
	- [Network Friendly](#Network%20Friendly)
	- [Security Principles](#Security%20Principles)
- [Users and Groups](#Users%20and%20Groups)
	- <a href="#user-group-mgt">User and Group Management</a>
- 
*Windows* uses a [Discretionary Access Control DAC](../Glossary%20(Global).md#Discretionary%20Access%20Control%20DAC) model that is very nuanced. *Windows* system administration, permission management, and security configurations is a long journey of discovery, trial and error, problem-solving, and best practices implementation meshes with organizational needs. It would be impossible to cover the entire scope of *Windows* security in a short overview, but we can cover the highlights with a "ten-thousand-foot view" somewhat easily.

## Architecture
First, let's compare [Linux File Permissions](../Linux%20Fundamentals/11%20File%20Permissions.md) to *Windows*. 
- On Linux, there are three sets of permissions (r-w-x), and three groups (user, group, other). *Windows* has many more sets of permissions. 
- Once authenticated on Linux, a user has "full rights" wherever their group ID or user ID is allowed access rights to the resources for the specific action they are trying to take. *Windows* uses [Security Identifiers](99%20Glossary%20(*Windows*).md#Security%20Identifiers%20SID) to create "access tokens" that interact with *Windows* security for any situation that requires authentication. 
- *Windows* has a far more robust and granular security system involve [Access Control Lists](../Glossary%20(Global).md#Access%20Control%20Lists), [Access Control Entries](../Glossary%20(Global).md#Access%20Control%20Entries), and [Security Identifiers](99%20Glossary%20(*Windows*).md#Security%20Identifiers%20SID), where Linux relies more heavily on proper permissions and [Sudoers](../Linux%20Fundamentals/10%20Elevated%20Linux%20Privileges.md#Sudoers%20a%20id%20sudoers%20a) via the [visudo](../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/visudo.md) command. 
- *Windows* is built on the concept of network permissions, the entire system built upon domains and security over a network. 
There are more differences than that, but those are some of the primary, baseline information. 
- The *Linux* root user is universally trusted, where on *Windows*, there are still confirmation prompts for certain activities performed by the Administrator and System users, managed by *User Access Control*

### Network Friendly
*Windows* has designed its security architecture heavily around the concept of networks. In fact, where Linux has commands such as has the simple [chmod](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/chmod.md) and [usermod](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/usermod.md) to manage users and permissions, the *Windows* command is named [net](../../Tools,%20Binaries,%20and%20Programs/*Windows*/Users%20and%20Security%20(not%20spellchecked)/net.md), and it handles the majority of user, group, and account related functions. 

*Windows* systems are pre-configured to have a domain, even if you are the only computer on the network, and users belong to a domain for networked security procedures. 

### Security Principles
Building on the concept of networked security, *Windows* has the concept of a [Security Principles](99%20Glossary%20(*Windows*).md#Security%20Principles) and [Security Identifiers](99%20Glossary%20(*Windows*).md#Security%20Identifiers%20SID). *Security Principles* does not mean "best practices" or "principles of security," it refers to any entity that can be authenticated by the operating system, such as a user account, a computer account, or a thread or process that runs in the security context of a user or computer account, or the security groups for these accounts. 

Every *security principle* is represented by a *SID*, a unique value of a varying length assigned by a trusted source that is used to identify a "trustee,"[^10]which is a user account, group account, or logon session. *Windows* maintains [Access Control List](../Glossary%20(Global).md#Access%20Control%20Lists) with [Access Control Entries](../Glossary%20(Global).md#Access%20Control%20Entries) that use these *SIDs* to identify the "trustee's" permissions. *Security principles* are the "subject" an operating system can authenticate to a resource.

The *SID* is associated with a user when they log on, and the [Local System Authority](99%20Glossary%20(Windows).md#Local%20System%20Authority) creates an "access token" for the user. This token is a protected object that contains the SID and any rights the user has. The SID (or the token) identifies the user in all interactions with *Windows* security for authorization. This architecture allows *Windows* to apply its security methodology to anything from a user to a group, or a thread or application. 

### User Account Control
As mentioned earlier, *Windows* does not fully trust the administrator or System users. [User Access Control](99%20Glossary%20(Windows).md#User%20Access%20Control) manages the "prompts" send to the user when the administrator token is requested for use by an application.

![UAC Prompt](Windows%20Fundamentals%20Photos/UAC_PROMPT.PNG)

This is helpful for maintaining the [Principle of Least Privilege](../Glossary%20(Global).md#Principle%20of%20Least%20Privilege) in a *Windows* system, particularly because the System user will often attempt to run processes in the background. Most are benign, even essential, but this still ensures that a new process that does not have access to the administrator access token cannot get it without a visual and manual confirmation by the user. 

From an attackers perspective, this means that if you try and perform some action on a *Windows* PC that triggers the UAC popup, any user on that PC will see the action and potentially trigger a response. 

## Users and Groups
### User and Group Management
<a id="user-group-mgt"></a>
There are several standard users and system accounts on every Windows installation. The three we are considered with are the Administrator, Guest, and System. Each one carries with it particular attributes, security ramifications, and a built in [Security Identifiers](99%20Glossary%20(Windows).md#Security%20Identifiers%20SID)
- **Administrator** &mdash; Built specifically to administer and manage the machine. Has full permissions on all files and directories. The most desirable target for an attacker during any type of engagement. It is the default account on creation, though another account will usually be created at the same time and given administrative permissions so the main Administrator account does not need to be used. This account cannot be deleted or locked, but it can be renamed or disabled. 
	- SID S-1-5-[domain]-500
	- Local Administrators group
- **Guest** &mdash; The Guest account is for temporary users and has restricted privileges. Disabled by default, but contains a blank password when enabled. From a security perspective, despite the limited privileges, it is an immediate foothold for an attacker if enabled but not secured properly. 
	- SID S-1-5-32-546
	- Guest group
- **SYSTEM** &mdash; Used by the OS to run services that themselves need a higher level of permissions. The default permissions for *SYSTEM* are that of an Administrator. While this account is not designed as a user account and cannot be logged in to, it can still be exploited and used to lead to potential privilege escalation or other types of compromise. Impersonating the *SYSTEM* user carries the same ramifications as compromising the Admin account. 

Modifying, adding, and removing user related information is handled with the [net](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/net.md) command and its arguments, such as `NET USER username password /ADD`. 

```
C:\Users\n0_ware>NET USER n0_ware s0m3p4ssw0rd /ADD
The command completed successfully.
```

In the same way but with a different options, system settings related to permissions can be modified with `NET`, such as modifying the minimum password length with `ACCOUNT`. 

```
C:\Users\s0me_where>NET ACCOUNTS /MINPWLEN:4
The command completed successfully.

C:\Users\s0me_where\GitHub\course-notes>net user n0_ware
User name                    n0_ware
Full Name
Comment
User's comment
Country/region code          000 (System Default)
Account active               Yes
Account expires              Never

Password last set            1/26/2022 8:04:45 PM
Password expires             3/9/2022 8:04:45 PM
Password changeable          1/26/2022 8:04:45 PM
Password required            Yes
User may change password     Yes

Workstations allowed         All
Logon script
User profile
Home directory
Last logon                   Never

Logon hours allowed          All

Local Group Memberships      *Users
Global Group memberships     *None
The command completed successfully.
```

You can get help with net via `net help`, and for options with `net help [option]`. 

### Command Execution
#### Runas
On the command line, we can "borrow" the identity of a user for running commands with the [runas](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/runas.md) command. While not as powerful or universal as the *Linunx* [sudo](../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md), it does allow us (or an attacker) to temporarily assume the identity of another, possibly higher privileged, user. 

#### cmd
When working in the *Windows* command prompt, you are using a program named `command.exe`, the basic *Windows* command line program. This is not always the case, such as via a remote connection or with remote code execution from an attackers perspective. Given that `command.exe` is just another binary, it can be invoked on an instance of itself to run another command. It can also be invoked via other code on the system to run commands. 

[^1]: #windows #fundamental #security 