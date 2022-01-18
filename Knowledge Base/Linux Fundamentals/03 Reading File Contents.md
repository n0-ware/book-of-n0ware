# Reading File Contents

###### Tags[^1]

[^1]: #head #cat #more #tail #less

## Table of Contents
- [cat](#cat)
- [more](#more)
- [less](#less)
- [head](#head)
- [tail](#tail)

## cat

The `cat` command reads out a files contents, regardless of how much is ine the file. 

```
linux@linux:~$cat file.txt
This is a file with text inside
```

There are several useful outputs. The argument `-n` prints each word on its own line:

```
linux@linux:~$cat file.txt
This
is
a
file
with
text
inside
```


## more

The `more` command prints one screen at a time, allowing the user to parse through page-by-page.

## less

The `less` command allows for both forward and backward navigation, listing the first ten lines in a file at a time. You can even watch a file for changes with the `+F` option. 

## head

The `head` command prints the top `N` lines of a file, specified with the `-n` flag. It defaults to the first ten lines witout an argument. For example. 

```
linux@linux:~$head -n 3 file.txt
```

## tail

The `tail` command is the opposite of `head`, printing the last `N` lines of a file, specified by the `-n` flag with the default being the last ten lines. 

```
linux@linux:~$less -n 3 file.txt
```
