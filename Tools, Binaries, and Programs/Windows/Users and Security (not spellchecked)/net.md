# net
###### Tags[^1]
The `net` command can be used to perform operations on Groups, users, account policies, shares, and so on.
## Syntax
```
C:\>net [ ACCOUNTS | COMPUTER | CONFIG | CONTINUE | FILE | GROUP | HELP | HELPMSG | LOCALGROUP | PAUSE | SESSION | SHARE | START | STATISTICS | STOP | TIME | USE | USER | VIEW ] [/?}]
```

Instead of `help net`, use `net help` or the `/?` flag after the `net` command. For help with `net` options, run `net help [option]`. For example, running `net accounts /?` gives detail on the actions you can take on the accounts on the system. 

***Common Net Commands***
- `net user [/add|/del]`
- `net localgroup [group] [username] [/add|/del]`
- `net accounts`
```
C:\Users\n0_ware>NET ACCOUNTS /?
The syntax of this command is:

NET ACCOUNTS
[/FORCELOGOFF:{minutes | NO}] [/MINPWLEN:length]
              [/MAXPWAGE:{days | UNLIMITED}] [/MINPWAGE:days]
              [/UNIQUEPW:number] [/DOMAIN]

```

From here you see the options you can set, such as `/MINPWLEN`. We can set the option such as in the example below. 

```			  
C:\Users\n0_ware>NET ACCOUNTS /MINPWLEN:4
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


### User
The `NET USER` command is very common for local enumeration, and with the right privileges, a new, high-privileged user can be added for [privilege escalation](../../../Knowledge%20Base/Vulnerabilities/Privilege%20Escalation%20(privsec).md#Windows). On its own, `NET USER` will output the list of user accounts, including guests and administrators. 

```
C:\Users\s0me_where>net users

User accounts for \\HARTPUTER

-------------------------------------------------------------------------------
Administrator            DefaultAccount           
Guest                    Wifey                    WDAGUtilityAccount
```

To add a user, we can use the `/ADD` option with the new username and password. 

```
C:\Users\n0_ware>NET USER n0_ware s0m3p4ssw0rd /ADD
The command completed successfully.
```

### Localgroup

List the users in a localgroup with `net localgroup [groupname]`. 


 [^1]: #windows #fundamental #users #security #privesc
