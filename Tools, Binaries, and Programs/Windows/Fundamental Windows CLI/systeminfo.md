# systeminfo
###### Tags[^1]
The `systeminfo` command is used to output a wealth of information about the system. Helpful to pair with [findstr](findstr.md) for filtering. Though not a built-in command (it is actually an executable `systeminfo.exe`), it functions a lot like a built-in command and even has a `help` menu (or `/?`).
## Syntax
```
C:\>COMMAND [options:] SOMETHING [drive:][path]filename
```

 **Common Arguments**
 - `/S` &mdash; Specify a remote system to connect to 
 - `/U [domain\]user` &mdash; Specifies a specific user context to run the command under
	-  `/P [password]` &mdash; Specify a password for the user with `/U`. Will prompt if no password is given
 - `/FO [format]` &mdash; Format output as. Can be `TABLE`, `LIST`, `CSV`. 

 See [local windows privsec](../../../Knowledge%20Base/Vulnerabilities/Privilege%20Escalation%20(privsec).md#Local%20Commands)
 
 [^1]: #windows #fundamental 