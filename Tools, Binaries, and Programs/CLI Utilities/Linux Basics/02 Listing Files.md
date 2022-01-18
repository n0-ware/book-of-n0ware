# Listing Files
###### Tags[^1]

[1^]: #ls

In these examples, `linux` is both the user and the hostname. 

## ls

You list files in a directory with the `ls` command:

```
linux@linux:~$ls
file1.txt file2.txt file3.txt
```

The argument `-1` lists all files on their own line: 

```
linux@linux:~$
file1.txt
file2.txt
file3.txt
```

Files that begin with a `.` are hidden. The argument `-a` lists all files, including hidden files:

```
linux@linux:~$ls -a
. .. file1.txt file2.txt file3.txt .hiddenfile.txt
```

The files `.` and `..` are references for `this directory` and `the directory above`, respectively. 

The argument `-l` lists file details, such as permissions:

```
linux@linux:~$ls -l
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file1.txt
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file2.txt
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file3.txt
```

These can be combined as you desire:

```
linux@linux:~$ls -la
drwxr-xr-x  2 linux linux 4096 Jan 17 20:03 .
drwxr-xr-x 27 linux linux 4096 Jan 17 20:03 ..
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file1.txt
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file2.txt
-rw-r--r--  1 linux linux    0 Jan 17 20:03 file3.txt
-rw-r--r--  1 linux linux    0 Jan 17 20:03 .hiddenfile.txt
```

Use `-R` to list files recusively. 

```
linux@linux:~$ls -lR
-rw-r--r-- 1 linux linux    0 Jan 17 20:03 file1.txt
-rw-r--r-- 1 linux linux    0 Jan 17 20:03 file2.txt
-rw-r--r-- 1 linux linux    0 Jan 17 20:03 file3.txt
drwxr-xr-x 2 linux linux 4096 Jan 17 22:30 newdir

./newdir:
total 0
-rw-r--r-- 1 linux linux 0 Jan 17 22:29 file4.txt
-rw-r--r-- 1 linux linux 0 Jan 17 22:29 file5.txt
```

Use `--color` to colorize the output. 

