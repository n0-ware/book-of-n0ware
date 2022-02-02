# tree
###### Tags[^1]

The `tree` command is used to output information in a tree from the current working directory or a specific directory. 
## Syntax
```
C:\>COMMAND [options:] SOMETHING [drive:][path]filename
```

 **Common Arguments**
 - `/F` &mdash; List the files in the directories returned.

## Example
The "SearchMe" directory has 10 subdirectories and is populated with files. Using the `/F` flag we can show both the structure of the directories and the files within. 

```
C:\Users\n0_ware\SearchMe>tree /F
C:.
│   file
│   file1
│   file2
│   file3
│   file4
│   file5
│   file6
│   file7
│
└───1
    │   file1
    │   file2
    │
    └───2
        │   file3
        │   file4
        │
        └───3
            │   file5
            │
            └───4
                └───5
                    └───6
                        │   file6
                        │
                        └───7
                            └───8
                                │   file7
                                │
                                └───9
                                    └───10
                                            foundme.txt
```





 [^1]: #windows #fundamental 
