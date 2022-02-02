# man
## Description
Most commands on the *Linux* command-line have what is known as a `man` page, accessed with the command:

```
man [command]
```

You navigate these menus by scrolling or using the arrow keys. A `man` page is searchable by first pressing the `/` key then typing your search string. Press enter and the screen will scroll down to the next occurrence of your search. 

Man pages are split into numbered sections on *Linux* systems. [^1]
| 1 | Description | 
| :-: | :-: | 
| 1 | General commands | 
| 2 | System calls | 
| 3 | Library functions, mostly around the "C" standard library | 
| 4 | Special files (usually devices found in `/dev`) and drivers | 
| 5 | File formats and conventions | 
| 6 | Games and screensavers | 
| 7 | Miscellaneous | 
| 8 | System administration commands and daemons | 

A specific portion of the man page can be accessed by using, where `#` is the section you want to access.

```
man # [command]
```

 At the top of any "man" page is the current numbered section you are on, and, and at the bottom of any "man" page are references to specific sections of interest related to this man page. This is an example of the man page for [usermod](Linux%20User%20Management.md#usermod) on the top and bottom. 
 
 ***Top***
 ![man page top](../../Photos%20(Tools)/MAN%20USERMOD%20TOP.png)

***Bottom***
![man page bottom](../../Photos%20(Tools)/MAN%20USERMOD%20BOTTOM.png)

Not all man pages contain all sections, but they will at the very least explain how to use the command, user flags, and functions of the command. 

To perform a "keyword search" with man, you can provide the `-k` flag. The `-k-` flag can also be used with a [regex](../../../Knowledge%20Base/Concepts/Regular%20Expressions%20(regex).md). This will list out the relevant man pages related to the keyword

[^1]:https://en.wikipedia.org/wiki/Man_page