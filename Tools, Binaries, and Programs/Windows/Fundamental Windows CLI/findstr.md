# findstr
###### Tags[^1]

The `findstr` command is used to find strings in files. 
## Syntax
```
C:\>findstr [options:] "strings" [drive:][path]filename
C:\>some-command | findstr [options:] "strings"
```

 [^1]: #windows #fundamental 

 **Common Arguments**
 - `/B` &mdash; Matches patterns at the beginning of a line 
 - `/E` &mdash; Matches patterns at the end of the line
 - `/S` &mdash; Searches recursively in current and subdirectories
 - `/R` &mdash; Searches with a regular expression 
 - `/I` &mdash; Search is not case sensitive
 - `/X` &mdash; Prints lines that are an exact match 
 - `/V` &mdash; Returns lines that do not match `strings`
 - `/N` &mdash; Add line number to output 
 - `/M` &mdash; Print the filename(s) only that contains `strings` 
 - `/F:file` &mdash; Reads a list of files from `file`
 - `/G:file` &mdash; Searches for a list of `strings` from `file`  
 - `/D` &mdash; Search a semicolon separated list of directories 
