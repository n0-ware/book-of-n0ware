# whoami
###### Tags[^1]
The `whoami` command has a number of ways it can be used, but primarily, it is used to get user name and group information, along with the related [Security Identifiers (SID)](../../../Knowledge%20Base/Windows%20Fundamentals/99%20Glossary%20(Windows).md#Security%20Identifiers%20SID) for the currently logged on user. 
## Syntax
```
C:\>whoami { [/USER] [/GROUPS] [/CLAIMS] [/PRIV] } [/FO format] [/NH]
```


 **Common Arguments**
 - `/USER` &mdash;  Displays the information for the current user, type of account, and SID attributes
 - `/GROUPS` &mdash; Displays group memebership for the current user, the type of account, and SID's
 - `/PRIV` &mdash; Displays privileges for the current user
 - `/LOGONID` &mdash; Displays the logon ID for the current user
 - `/ALL` &mdash; Displays user name, groups, claims, privileges, and SID's for the current user. 

## Example

```
USER INFORMATION
----------------

User Name       SID
=============== ==============================================
homePC\n0_ware S-1-5-21-2184681898-1587991450-2606260337-1001
```
 [^1]: #windows #fundamental 
		