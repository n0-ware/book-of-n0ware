# cd
###### Tags[^1]
Stands for **change directory** and is the *Windows* command used to change from one directory to another. The syntax can be [absolute](#absolute) or [relative](#relative). 

## Syntax 
```
C:\Users\n0-ware>cd \Path\To\Directory # Absolute
C:\Users\n0-ware>cd ..\..\Path\To\Directory # Relative
C:\Users\n0-ware>cd Directory # Assumes the directory is in the same directory you are operating in. 
```

You can navigate "up" a directory, or several directories at once, with `..`. For example

```
C:\Users\n0-ware>echo %cd%
C:\Users\n0-ware

C:\Users\n0-ware>echo %cd%
C:\Users\n0-ware

C:\Users\n0-ware>cd ..

C:\Users>echo %cd%
C:\Users

C:\Users>
```
 
 Repeating this, separated by `\`, will increase the amount you move up. For example, `..\..\` moves up two directories. 
 
**Error Message**
```
C:\Users>cd somedir
The system cannot find the path specified.
```

To return to the root of the current drive, simply type `cd\`. Like *Linux*, you can easily navigate back to the current user's home directory. Instead of `~`, you use the [Environment Variable](../../../Knowledge%20Base/Windows%20Fundamentals/05%20Windows%20Environment%20and%20System%20Information.md#Environment%20Variables) `homepath` via `cd %homepath%`

### absolute

***Absolute*** references refer to referencing a file or directory by starting with the drive letter, such as `C:\`. For example, to navigate to the `Documents` directory from anywhere on the system:

```
C:\Users\n0-ware\Downloads>cd C:\Users\n0-ware\Documents

C:\Users\n0-ware\Documents>
```

For scripts, programs, configurations, etc., that rely on a specific directory, *absolute* references are best.

### relative

A ***relative*** reference is a file or directory reference "relative" to the current working directory. This works because of where you are in the system. From the user's primary directory, which is `\home\linux`, the file tree looks like this:

```
C:\Users\n0-ware\
			\Documents
			\Downloads
			\Pictures
			\...
```

To move from `Documents` to `Downloads`, for example, use the syntax:

```
C:\Users>cd ..\Downloads
```

To reference a file in the `Downloads` directory, the syntax is similar:

```
C:\Users>type ..\Downloads\somefile.txt
```

[^1]: #fundamental #windows #navigation