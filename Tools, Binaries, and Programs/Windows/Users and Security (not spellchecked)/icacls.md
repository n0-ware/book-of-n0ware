# icacls
###### Tags[^1]
The `icacls` command is used to view and interact with *Windows* permissions. 

## Syntax
```
C:\>icacls [fil[/grant|/deny] SID:perm[...]
```
The potential syntax for this command is vast. Review the `help` of [documentation](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/icacls) for further information. 

Used without any additional options, `icacls` will list the current permissions of the file. 
```
C:\Users>icacls permfile.txt
permfile.txt NT AUTHORITY\SYSTEM:(I)(F)
             BUILTIN\Administrators:(I)(F)
             BUILTIN\Users:(I)(RX)
             Everyone:(I)(RX)
```

Note that the `I` designates that the permissions were inherited from the parent, and the second set, contained in the `()`, designates the specific permissions applied. 

The simple rights that `icacls` can grant are listed below:
```
N - no access
F - full access
M - modify access
RX - read and execute access
R - read-only access
W - write-only access
D - delete access
```
Information on inheritance is also listed at the bottom of the `help`. 
```
(OI) - object inherit
(CI) - container inherit
(IO) - inherit only
(NP) - don't propagate inherit
(I) - permission inherited from parent container
```


## Examples
### Users
Grant or deny permissions with the `/grant` and `/deny` options, supplying the user as `Sid` and the permissions you want. 

```
C:\Users>icacls permfile.txt /grant n0_ware:(RX)
processed file: permfile.txt
Successfully processed 1 files; Failed processing 0 files

C:\Users>icacls permfile.txt
permfile.txt HARTPUTER\n0_ware:(RX)
             NT AUTHORITY\SYSTEM:(I)(F)
             BUILTIN\Administrators:(I)(F)
             BUILTIN\Users:(I)(RX)
             Everyone:(I)(RX)		 
```

See `help icacls` or [here](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/icacls)for more details on using the command and modifying permissions.

### Groups
Add permissions to an entire group with `/grant:r [Group]:(..)`

```
C:\Users>icacls permfile.txt /grant:r "Users":(F)
processed file: permfile.txt
Successfully processed 1 files; Failed processing 0 files

C:\Users>icacls permfile.txt
permfile.txt BUILTIN\Users:(F)
             HARTPUTER\n0_ware:(RX)
             NT AUTHORITY\SYSTEM:(I)(F)
             BUILTIN\Administrators:(I)(F)
             BUILTIN\Users:(I)(RX)
             Everyone:(I)(RX)
```
 **Common Arguments**
 - `/T` &mdash; Executes the change on recursively, meaning on all subfolders 
 - `/C` &mdash; Continue, regardless of errors 
 - `/L` &mdash; For use with symbolic links. Causes the operation to execute only on the link, not the target.  
 - `/grant` &mdash; Used to grant permissions 
 - `/deny` &mdash; Used to deny permissions 
 - 



 [^1]: #windows #fundamental 
