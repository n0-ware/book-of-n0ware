# Part 3 - File and Folder Management

## Lecture 3-1 | Key Points about Files

> **Instructor Note** &mdash; Brief conversation about the nature of files and file types. Key points will be running files with `./`.

- All items in Linux are a file if they are not a directory
- All files have permissions (more on that later)
	- These are the sets of `rwx` you see to the left of a file with `ls -la`
- Extensions on Linux **do not matter** unless otherwise specific. 
	- i.e., an application is looking for file by extension. 
	- Using extensions is a **best practice** for file system organization. 
	- Two of the most common on Linux are `.txt` and `.sh`. 
- Manipulating files on the CLI is unforgiving. 
	- Deletions are permanent
	- There is no undo
	- Files can easily be overwritten
		- The legend of `rm -rf /
- Files are ran by simply referencing them **BUT** with `./` before the filename. 
	- They must also be executable (highlighted green in `.zsh`)
- File and folder names **without spaces** are the easiest to manipulate. If your target has spaces you:
	- Encase it in quotations, such as `echo "some file with spaces.txt"` or
	- "Escape" the sapces with `\`, such as `echo "some\ file\ with\ spaces.txt"`
- Wildcards are "wildly" helpful
	- `*` stands for "anything"
	- `?` stands for one single character
- 

## Lecture 3-2 | Basic File Manipulation Commands

### Reding File Contents

#### cat

![[03 Reading File Contents#cat]]

#### more

![[03 Reading File Contents#more]]

#### less

![[03 Reading File Contents#less]]

#### head

![[03 Reading File Contents#head]]

#### tail

![[03 Reading File Contents#tail]]

### File Manipulation

#### Create a file - touch

![[05 File Management#touch]]

#### Remove a File or Directory - rm

![[05 File Management#rm]]

#### Make a Directory - mkdir

![[05 File Management#mkdir]]

#### Move a File or Directory

![[05 File Management#mv]]

#### Copy a File or Directory - cp

![[05 File Management#cp]]

#### Linking

> **Instructor Note** &mdash; Mention the capability. Not necessarily the requirement. More of a "system admin" task

![[05 File Management#ln]]

### Using Wildards

![[05 File Management#Wildcards]]

##

> Finish with them submitting an md5 of the correct solution

## Demo 3-1 | The Forest

> **Instructor Note** &mdash; Overall, students should just play around and create files. Have them create a backup of the forest right away so they can have a fresh one on hand. 

Navigate to the S3 bucket and download `Forest.tar.gz`. Open a terminal and run the command

```Bash
# Note the absolute reference!
$$$ tar -xzvf ~/DownloadsForest.tar.gz
```

Where options are as follows:

-   **-z** : Uncompress the resulting archive with gzip command.
-   **-x** : Extract to disk from the archive.
-   **-v** : Produce verbose output i.e. show progress and file names while extracting files.
-   **-f data.tar.gz** : Read the archive from the specified file called data.tar.gz.

## Navigation
- [ ] ls
- [ ] cat
- [ ] more
- [ ] less head
- [ ] tail
- [ ] echo

## File Manipulation

- [ ] touch
- [ ] rm
- [ ] mkdir
- [ ] mv
- [ ] cp
- [ ] wildcards
- [ ] links (mention)

![[Pasted image 20221025155209.png]]