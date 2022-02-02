# taskkill
###### Tags[^1]
The `taskkill` command is used to terminate tasks by either PID or image name. Use [tasklist](tasklist.md) to identify tasks you want to kill. 
## Syntax
```
C:\>taskkill [/S system [/U username [/P [password]]]] { [/FI filter] [/PID processid | /IM imagename] } [/T] [/F]

```

## Examples

Killing an instance of `notepax.exe`

```
C:\Users>tasklist /FI "IMAGENAME eq notepad.exe"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
notepad.exe                  23824 Console                    1     14,520 K

C:\Users>taskkill /PID 23824
SUCCESS: Sent termination signal to the process with PID 23824.

C:\Users>tasklist /FI "IMAGENAME eq notepad.exe"
INFO: No tasks are running which match the specified criteria.
```


 **Common Arguments**
 - `/U` &mdash; Specifies the user context to run the command 
 - `/P` &mdash; Gives the password for the user context 
 - `/V` &mdash; Makes the output more verbose.  
 - `/FI filter` &mdash; Filters by criteria. See the `/?` page for available filters
	 - `PID` is a commonly used filter, as well as `Services` for "Service name" and `MODUELS` for DLL name
	 - Operators can be used with filters, such as `eq` and `ne` for equals and does not equal, as well as greater/less than operators and their counterparts. 
	 - Filters are wrapped in quotes, `"USERNAME eq n0_ware"` 
 - `/F` &mdash; Kill a task forcefully. 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental 
