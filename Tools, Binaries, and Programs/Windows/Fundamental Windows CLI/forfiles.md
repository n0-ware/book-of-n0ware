# forfiles
###### Tags[^1]
The `forfiles` command is a robust file for executing commands on a single or set of files. It also is very useful for locating files on the system. 

## Syntax
```
C:\>forfiles [/P pathname] [/M searchmask] [/S] [/C command] [/D [+ | -] {MM/dd/yyyy | dd}]
```

 **Common Arguments**
 - `/P` &mdash; The path we want to search 
 - `/M` &mdash; The "search mask" or "strings" that we want to search for. Default is wildcard `*`, and can be anything including additional wildcards.  
 - `/C` &mdash; The command to execute. The default is `cmd /c echo @file` where files it the name of the file. `@path` is another good one for locating the path to the file. 
 - `/S` &mdash; Searches subdirectories
 
## Example

Let's take the `chrome.exe` file as an example. We want to find it in the `C:\Program Files` directory. We can search that directory with `/P`, search recursively with `/S`, provide the search string with `/M`, and customize our command with `/c "cmd /c echo @path"`

```
C:\Users\Eddie\SearchMe>forfiles /P "C:\Program Files" /S /M chrome.exe /c "cmd /c echo @PATH"

"C:\Program Files\BurpSuiteCommunity\burpbrowser\85.0.4183.121-1\chrome.exe"
"C:\Program Files\Google\Chrome\Application\chrome.exe"
```

 [^1]: #windows #fundamental 
