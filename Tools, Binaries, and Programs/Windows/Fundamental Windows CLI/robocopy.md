# robocopy
###### Tags[^1]
The upgraded version of the [copy](copy.md) command on windows, `robocopy` has some very robust features to enable higher performance, security checks, skipping of unwanted items, and more. 

View the help page [here](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)

## Syntax
```
C:\>robocopy <source> <destination> [<file>[ ...]] [<options>]
```


 **Common Arguments**
 - `/s` &mdash; Copies subdirectories, automatically excluding empty directories 
 - `/e` &mdash; Copies subdirectories, automatically including empty directories
 - `/z` &mdash; Allows the copy to be restarted if it is interrupted. 


 [^1]: #windows #fundamental #files
