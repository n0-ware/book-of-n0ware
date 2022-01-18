# diff	

## Description

With the `diff` command, you can identify the differences between two files. `diff` can be compared to [`comm`](../../../../course-notes/Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/comm.md), except `diff` is more complex and had more functionality. 

## Syntax
`diff` compares the *first* file to the *second* for the sake of special characters. 

```
diff [args] file1 file2
```

- `-c` &mdash; Conext format
- `-u` &mdash; Unified format
- `-i` &mdash; Makes the comparison case insensitive
- `-B` &mdash; Ignore blank lines

Special characters:

- `a` &mdash; Means this line was added
- `c` &mdash; Means this line was changed
- `d` &mdash; Means this line was deleted
- `>` &mdash; Line corresponds to the first file
- `<` &mdash; Line corresponds to the second file
- `+` &mdash; This line needs to be added to make them the same
- `-` &mdash; This line needs to be removed to make them the same
- `!` &mdash; This line was changed between the two files

## Examples

***Using context format***

```
┌──(kali㉿kali)-[~/test]
└─$ diff -c users-1.txt users-2.txt 
*** users-1.txt 2022-01-18 08:27:44.222076265 -0500
--- users-2.txt 2022-01-18 08:28:04.474076883 -0500
***************
*** 1,7 ****
  ben
  bill
  carl
- gerry
  jason
! jeff
! rob
--- 1,8 ----
+ adam
  ben
  bill
+ bob
  carl
  jason
! john
! robert
```

Linux will colorize the output if using *Z Shell*

![diff -c](../../../../book-of-n0ware/Tools,%20Binaries,%20and%20Programs/Photos%20(Tools)/diff%20with%20-c.png)

***Diff with unified format***
```
┌──(kali㉿kali)-[~/test]
└─$ diff -u users-1.txt users-2.txt                                              1 ⨯
--- users-1.txt 2022-01-18 08:27:44.222076265 -0500
+++ users-2.txt 2022-01-18 08:28:04.474076883 -0500
@@ -1,7 +1,8 @@
+adam
 ben
 bill
+bob
 carl
-gerry
 jason
-jeff
-rob
+john
+robert
                 
```

***Standard diff***
```
┌──(kali㉿kali)-[~/test]
└─$ comm users-1.txt users-2.txt
        adam
                ben
bill
        Bill
        bob
                carl
gerry
                jason
jeff
        John
rob
        robert


┌──(kali㉿kali)-[~/test]
└─$ diff users-1.txt users-2.txt
0a1
> adam
2c3,4
< bill
---
> Bill
> bob
4d5
< gerry
6,7c7,8
< jeff
< rob
---
> John
> robert

```

The characters here can be hard to read at first, but here is the breakdown
- `0a1` &mdash; From the beginning, `0`, to line `1`, you need to add "adam" from the first file. 
- `2c3,4` &mdash; After line 2 in file one, line 3 needs to be changed from `bill` to `Bill` and line 4 needs `bob` added. 
- `4d5` &mdash; Line 4 in file one, `gerry`, needs to be deleted.
- `6,7c7,8` &mdash; Line 6, `jeff`, needs to be removed, line 7 needs to be changed from `rob` to `John`, and line 8 needs to be added as `robert`
