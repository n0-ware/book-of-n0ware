# Navigation
###### Tags[^1]

[^1]: #cd #pwd #absolute #relative #file

In these examples, `linux` is both the user and the hostname. 

## cd
Stands for **change directory** and is the *Linux* command used to change from one directory to another. The syntax can be **absolute** or **relative**. 

**Syntax**
```
linux@linux:~$cd /Path/To/Directory # Absolute
linux@linux:~$cd ../../Path/To/Directory # Relative
linux@linux:~$cd Directory # Assumes the directory is in the same directory you are operating in. 
```

You can navigate "up" a directory, or several directories at once, with `..`. For example

```
linux@linux:~$pwd
/home/linux/Documents
linux@linux:~$cd ..
linux@linux:~$pwd
home/linux
```
 
 Repeating this, separated by `/`, will increase the amount you move up. For example, `../../` moves up two directories. 
 
**Error Message**
```
cd: no such file or directory: /<Directory_Name_Attempted>
```

## pwd

Stands for **print working directory** and is used to print the current directory the user is in to screen. 

**Syntax**
```
linux@linux:~$pwd

linux@linux:~$/home/linux/Documents # Prints whatever directory the user is in
```

## file

Prints the type of file referenced in the command. 

**Syntax**:
```
linux@linux:~$file <File_to_Reference>
```


## absolute

***Absolute*** references refer to referencing a file or directory by starting with the root `/` directory. For example, to navigate to the `Documents` directory from anywhere on the system:

```
cd /home/linux/Documents
```

For scripts, programs, configurations, etc., that rely on a specific directory and must eb able to run from anywhere, *absolute* references are best.

## relative

A ***relative*** reference is a file or directory reference "relative" to the current working directory. This works because of where you are in the system. From the users "home" directory, which is `/home/linux`, the file tree looks like this:

```
/home/linux
	/Documents
	/Downloads
	/Pictures
	/...
```

To move from `Documents` to `Downloads`, for example, use the syntax:

```
linux@linux:~$cd ../Downloads
```

To reference a file in the `Downloads` directory, the syntax is similar:

```
linux@linux:~$file ../Downloads/somefile.txt
```

The `~` symbol represents the user's home directory, `/home/linux`. You may use this in ***relative*** references. To navigate to `Documents` from anywhere, the syntax is:

```
linux@linux:~$cd ~/Documents