# # File Management

###### Tags[^1]

[^1]: #linux #fundamentals #mkdir #touch #rm #filemanagement
## Table of Contents
- [touch](#touch)
- [rm](#rm)
- [mkdir](#mkdir)
- [mv](#mv)
- [cp](#cp)
- [cat](#cat)
- [ln](#ln)
	- [Softlink](#Softlink)
	- [Hardlink](#Hardlink)

## touch

The `touch` command creates an empty file

**Syntax**
```
touch filename.txt
```

## rm

To remove a file, use `rm`. Remove directories with the `-r` flag. 

**Syntax**
```
rm filename.txt
rm -r dirname/
```

> There is no undo!

## mkdir
To make a directory, use `mkdir`. You make a path with the `-p` flag. 

**Syntax**

```
mkdir dirname
mkdir -p dirname/anotherdirname
```

## mv

To move a file, either with the same name or with a new name, use `mv`. 

**Syntax**
```
┌──(kali㉿kali)-[~/test]
└─$ touch file.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
file.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ mkdir newdir
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
file.txt  newdir
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ mv file.txt newdir 
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
newdir

```

```
┌──(kali㉿kali)-[~/test]
└─$ touch somefile.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
somefile.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ mv somefile.txt newfilename.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
newfilename.txt
```


## cp

You can copy a file with `cp`. This creates a file with the exact same contents but with a different name. Linux will not warn you if you are about to overwrite a file. 

```
┌──(kali㉿kali)-[~/test]
└─$ touch fileone.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
fileone.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cp fileone.txt filetwo.txt
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ ls
fileone.txt  filetwo.txt
```

## cat

Use `cat` to print the contents of a file. Note that `>` is used to "pipe" the output of echo into `fileone.txt` so we can print it back out. 

```
┌──(kali㉿kali)-[~/test]
└─$ echo "Hello world" > fileone.txt 
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cat fileone.txt           
Hello world
```

## ln

We can use *symlinks* to link to a file from another directory with `ln`. 

### Softlink
The `-s` flag crates a "soft link."

```
┌──(kali㉿kali)-[~/Documents]
└─$ cd othertest  
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ls
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ln -s ~/test/fileone.txt 
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ls -la                  
total 8
drwxr-xr-x 2 kali kali 4096 Jan 17 22:39 .
drwxr-xr-x 5 kali kali 4096 Jan 17 22:38 ..
lrwxrwxrwx 1 kali kali   27 Jan 17 22:39 fileone.txt -> /home/kali/test/fileone.txt
```

Changing the text inside `fileone.txt` will change what prints when we `cat` the symlink. 

```
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ln -s ~/test/fileone.txt symlink.txt 
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ls -la                                  
total 8
drwxr-xr-x 2 kali kali 4096 Jan 17 22:41 .
drwxr-xr-x 5 kali kali 4096 Jan 17 22:38 ..
lrwxrwxrwx 1 kali kali   27 Jan 17 22:41 symlink.txt -> /home/kali/test/fileone.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat symlink.txt 
Hello world
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ echo "Bye everyone" > ~/test/fileone.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat symlink.txt 
Bye everyone

```

### Hardlink
To create a "hardlink" we use `ln` without any arguments. A hardlink actually copies the file, and it will remain after we delete it. 

```
┌──(kali㉿kali)-[~/test]
└─$ touch hardfile.txt        
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ echo "I am a hardfile" > hardfile.txt 
                                                                                     
┌──(kali㉿kali)-[~/test]
└─$ cd ../Documents/othertest 
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ln ~/test/hardfile.txt hardlink.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ ls -la                             
total 12
drwxr-xr-x 2 kali kali 4096 Jan 17 22:44 .
drwxr-xr-x 5 kali kali 4096 Jan 17 22:38 ..
-rw-r--r-- 2 kali kali   16 Jan 17 22:44 hardlink.txt
lrwxrwxrwx 1 kali kali   27 Jan 17 22:41 symlink.txt -> /home/kali/test/fileone.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat hardlink.txt         
I am a hardfile
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ echo "I am a changed hardfile" > ~/test/hardfile.txt 
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat hardlink.txt 
I am a changed hardfile
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ rm ~/test/hardfile.txt 
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat hardlink.txt 
I am a changed hardfile
```

## Wildcards

Wildcards can be used to reference either a large number of files at once or to reference a specific file where you are only sure of a certain number of the characters in the filename. Each `*` stands for any number of characters. For example, running `cat *` will run `cat` on every file in the directory. On the other hand, running `cat *.txt` will run `cat` only on files that start with anything but end with `.txt`. You can use wildcards in any combination. For example, the file `i_123_am_456_a_789_file.txt` can be referenced with `i*am*a*file*`. 

```
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ touch i_123_am_456_a_789_file.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ echo "I love wildcards" >  i_123_am_456_a_789_file.txt
                                                                                     
┌──(kali㉿kali)-[~/Documents/othertest]
└─$ cat i*am*a*file*
I love wildcards
```

Wildcards can also be used with ranges, such as removing any files with the characters `a-f` or numbers. 

```
rm *[a-f]*
rm *[0-9]*
```

