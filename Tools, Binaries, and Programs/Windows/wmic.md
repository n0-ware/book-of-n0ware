# wmic
###### Tags[^1]
The **Windows Management Instrumentation Command Line** tool `wmic` is a utility that allows users to interact with **Windows Management Instrumentation (WMI)** operations via the command prompt. Its uses are vast and can be found [here](https://docs.microsoft.com/en-us/windows/win32/wmisdk/wmic)

## Examples
### Processes
Using `wmic` and some scripting syntax, we can get the Parent Process ID (PPID) of a running process.
`wmic Process where (ProcessID=PROCID_HERE) get Caption,ParentProcessID``
```
C:\Users>wmic process where (processid=4736) get Caption,ParentProcessid
Caption      ParentProcessId
firefox.exe  10480
```

Conversely, we can view the children of the parent with a different `wmic` command. 
`wmic Process where (ParentProcessID=PROCID_HERE) get Caption,ProcessID`
```
C:\Users>wmic process where (ParentProcessID=10480) get Caption,ProcessID
Caption      ProcessId
firefox.exe  4736
firefox.exe  13076
firefox.exe  5236
firefox.exe  25720
firefox.exe  9112
firefox.exe  12060
```

### Services

`wmic service list`
It is good to pipe this into a filter to bring down the quantity of output. 
 [^1]: #windows #advanced 