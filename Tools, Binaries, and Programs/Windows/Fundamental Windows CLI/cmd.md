# cmd
###### Tags[^1]

The `cmd` is used to invoked the `command.exe` binary on *Windows*. It can be used within an existing command prompt, or in another scenario where you want to designate a command to run with `command.exe`. 

A good example of this is in the [forfiles](forfiles.md) command where the`/C` flag allows us to run commands on the files we find in the search, using the `cmd` command to execute the commands we want, such as `cmd /c echo @path`.

## Syntax
```
C:\>cmd /c [command]

C:\>cmd /c echo "I am commanding!"
I am commanding!
```

**Used in the context of another command**
```
C:\>forfiles /P C:\Users\n0_ware /S /M *.txt /C "cmd /C echo The name of the file is @file"
```

 [^1]: #windows #fundamental 

 