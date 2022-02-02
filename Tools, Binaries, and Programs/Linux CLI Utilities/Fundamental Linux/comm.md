# comm
## Description

The `comm` command is used to compare text files, printing to screen the lines in each file that are unique. `comm` can be compared to [`diff`](diff.md), but `comm` is far more simple. This is excellent for comparing two similar lists, log files, and so on. It displays the information in three columns. The first is unique to the first list, the second is unique to the second, and the third is items that are shared. 

## Examples 
The `-n` flag can suppress any of the columns, where `n` is any column numbers, 1-3. 

***Comparing User Lists***
```
┌──(kali㉿kali)-[~]
└─$ cat users-1.txt                    
ben
bill
carl
gerry
jason
jeff
rob
                                                                                     
┌──(kali㉿kali)-[~]
└─$ cat users-2.txt 
adam
ben
bill
bob
carl
jason
john
robert
                                                                                     
┌──(kali㉿kali)-[~]
└─$ comm users-1.txt users-2.txt
        adam
                ben
                bill
        bob
                carl
gerry
                jason
jeff
        john
rob
        robert
```

***Suppressing columns 1 and 2***
```
┌──(kali㉿kali)-[~]
└─$ comm -12 users-1.txt users-2.txt 
ben
bill
carl
jason
```                                                                     