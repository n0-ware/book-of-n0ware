# Redirecting Output

## Table of Contents
- [Streams](#Streams)
- [Piping and Redirection](#Piping%20and%20Redirection)
	- [Redirect](#Redirect)
	- [Append](#Append)
	- [Read](#Read)
	- [STDERR](#STDERR)
	- [Pipe](#Pipe)
## Streams
In *Linux*, there are three data streams by default
- **STDIN (0)** &mdash; The *standard input* on which data is fed into a program. Essentially, the part of the terminal that accepts our input
- **STDOUT (1)** &mdash; The *standard-output* in the opposite, essentially how data is printed by a program, in most cases, what we see on the terminal
- **STDERR (2)** &mdash; The *standard error* is for error messages, also printed to the terminal by default

## Piping and Redirection
These are the means that a user may connect the three streams between different programs and files, allowing them to point data wherever they want it to flow. For example, it is common practice to pipe the ***STDOUT*** of one program, like `echo` or `cat`, into the ***STDIN*** of another program, something like [Grep and Egrep](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/Grep%20and%20Egrep.md) or[cut](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/cut.md). 

There are several symbols for piping and redirection. 

### Redirect

Often used with `echo`, the `>` operator allows us to save the ***STDOUT*** of one program to a file instead of printing to screen:

```
┌──(kali㉿kali)-[~/test]
└─$ echo "Hello world"
Hello world

┌──(kali㉿kali)-[~/test]
└─$ echo "Hello world" > file.txt                         
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat file.txt    
Hello world
```

We can use the output of any program as the input for `>`: 

```
┌──(kali㉿kali)-[~/test]
└─$ ls -la           
total 16
drwxr-xr-x  2 kali kali 4096 Jan 17 23:34 .
drwxr-xr-x 27 kali kali 4096 Jan 17 22:59 ..
-rw-r--r--  1 kali kali   12 Jan 17 23:32 file1.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:33 file2.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:33 file3.txt
-rw-r--r--  1 kali kali  373 Jan 17 23:34 list.txt
lrwxrwxrwx  1 kali kali   11 Jan 17 23:33 passwdlink -> /etc/passwd
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la > list.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat list.txt 
total 12
drwxr-xr-x  2 kali kali 4096 Jan 17 23:34 .
drwxr-xr-x 27 kali kali 4096 Jan 17 22:59 ..
-rw-r--r--  1 kali kali   12 Jan 17 23:32 file1.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:33 file2.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:33 file3.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:34 list.txt
lrwxrwxrwx  1 kali kali   11 Jan 17 23:33 passwdlink -> /etc/passwd
```

We can redirect to a file that does not exist, therefore creating it. 

```
┌──(kali㉿kali)-[~/test]
└─$ ls -la           
total 8
drwxr-xr-x  2 kali kali 4096 Jan 17 23:37 .
drwxr-xr-x 27 kali kali 4096 Jan 17 22:59 ..
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ echo "Create a file" > newfile.txt    
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la 
total 12
drwxr-xr-x  2 kali kali 4096 Jan 17 23:38 .
drwxr-xr-x 27 kali kali 4096 Jan 17 22:59 ..
-rw-r--r--  1 kali kali   14 Jan 17 23:38 newfile.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat newfile.txt         
Create a file
```

### Append

Like `>`, a double `>>` "appends" the output to the end of the target file, avoiding any overwriting that may occur with a single `>`. 

```
┌──(kali㉿kali)-[~/test]
└─$ echo "First Line" >  dont_overwriteme.txt                                    1 ⨯
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ echo "Second Line" >> dont_overwriteme.txt 
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat dont_overwriteme.txt 
First Line
Second Line
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ echo "Overwite" > dont_overwriteme.txt    
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat dont_overwriteme.txt 
Overwrite
```

### Read

The opposite symbol, `<`, lets us "read in" data from a file. Using the `wc` command tests the byte count, among other things, of a file. 

```
┌──(kali㉿kali)-[~/test]
└─$ echo "I have 16 bytes" > bytefile.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat bytefile.txt 
I have 16 bytes
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ wc -m < bytefile.txt                 
16
```

### STDERR

If you want to capture only errors, you use the number `2` before the `>`, `>>`, or `<` symbol. 

> There is a device built into *Linux* located in the folder `/dev/null` which is useful for redirecting uninteresting output. This folder automatically deletes, forgets, and completely purges any output directed to it. 
> 
> For example, if I wanted to redirect error output only from a command, I might use `2> /dev/null` at the end of my command. 

```
┌──(kali㉿kali)-[~/test]
└─$ touch i_exist.txt                                                            1 ⨯
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la                
total 8
drwxr-xr-x  2 kali kali 4096 Jan 17 23:42 .
drwxr-xr-x 27 kali kali 4096 Jan 17 23:40 ..
-rw-r--r--  1 kali kali    0 Jan 17 23:42 i_exist.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la i_exist.txt > are_you_real.txt 
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat are_you_real.txt 
-rw-r--r-- 1 kali kali 0 Jan 17 23:42 i_exist.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la i_dont_exist.txt 2>> are_you_real.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat are_you_real.txt                                                         2 ⨯
-rw-r--r-- 1 kali kali 0 Jan 17 23:42 i_exist.txt
ls: cannot access 'i_dont_exist.txt': No such file or directory
```

### Pipe

We can use the output from one program as the input for another program via *piping* with the `|` symbol. This is extremely common with `cat` and `grep`. If we want to output the `/etc/passwd` information for our user, specifically, we can do this easily:

```
┌──(kali㉿kali)-[~/test]
└─$ cat /etc/passwd | grep kali
kali:x:1000:1000:Kali,,,:/home/kali:/usr/bin/zsh
```

Or, we can identify the number of lines in our output by piping `ls -la` into `wc -l`. 

```
┌──(kali㉿kali)-[~/test]
└─$ ls -la | wc -l                              
5
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -la        
total 12
drwxr-xr-x  2 kali kali 4096 Jan 17 23:43 .
drwxr-xr-x 27 kali kali 4096 Jan 17 23:40 ..
-rw-r--r--  1 kali kali  114 Jan 17 23:43 are_you_real.txt
-rw-r--r--  1 kali kali    0 Jan 17 23:42 i_exist.txt

```

Imagine we want to list unique lines in a log. We can do this by piping into `uniq`. Or, let's say we want to sort the contents of a directory alphabetically, we can use `sort`. 

```
┌──(kali㉿kali)-[~/test]
└─$ cat not_unique.txt         
1
1
1
2
2
2
3
4
4
4
5
5
5
5
5
5
6
7
8
9

                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat not_unique.txt | uniq
1
2
3
4
5
6
7
8
9

┌──(kali㉿kali)-[~/test]
└─$ touch a b c d e f g h i j k l m
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ touch z y x w v u t s r q p o n

┌──(kali㉿kali)-[~/test]
└─$ ls -t         
n  o  p  q  r  s  t  u  v  w  x  y  z  a  b  c  d  e  f  g  h  i  j  k  l  m
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls -t | sort
a
b
c
d
e
f
g
h
i
j
k
l
m
n
o
p
q
r
s
t
u
v
w
x
y
z
```

We can count the number of users on a system other than root, for example, with `cat /etc/passwd | grep -vi root | wc -l`