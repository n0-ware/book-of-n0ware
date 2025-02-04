
## Housekeeping

### CyberLAB

- What is a VM?
- CyberLAB and Guacamole
- Updating vs Upgrading
- Virtualizing at home
- The Control Panel
- Getting help

### Basics

- How to take screenshots
	- Windows and Mac
- Copy Paste
- Getting help
	- Layers of support
		- Research
		- Group
		- Big Group/TA
		- Office Hours
		- Instructor
		- Tech Support

## Part 1 - Linux and Shells

### Linux Shell

> Use the lab screen to demonstrate

Key points:
1. Four parts of *Linux*
2. Flavor = Software on Install and base configurations

#### The Command Line

- CLI is the most common way people interact with *Linux-based* operating systems. 
- **Even though most come with a GUI**
- Why?
	- Easy navigation
	- Effective interaction with core system processes
	- Precision *"CLI"* tools to the use-case
	- Lightspeed ahead off *"point-and-click"* interaction for It-related tasks
- The *CLI* was built before there was a desktop. 
	- It has growth with, not replaced
	- Many *"built-in"* commands started as full-fledged programming languages, such as `awk`
	- See [awk](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/) - `https://www.reddit.com/r/ObsidianMD/comments/txnb4t/why_is_copy_pasting_from_obsidian_to_another_app/`
- Terminals, across all operating systems, have the same general principles, look, and feel
	- Does not take away ***vast*** differences among them
	- `zsh` vs `bash` for example
	- Software, direction of the "slash", etc., may all change
	- Ability to interact with the system essentially the same

> Brief talk about Kali and the reasons we use it
> Talk about the other systems we use as well. 

#### Shells

- A *"Shell"* is just what we call the terminal. 
	- Process commands via *input* and *output*, or **I/O**. 
	- Many types of shells
	- Specific to *Linux*...
	-   **sh** — The "Bourne SHell", this is the foundation for nearly every shell in use today. It holds the most crucial, base-line tasks, including command interpretation and is itself a scripting language.
	-   **Bash** — The _Bourne-Again SHell_ was designed to replace _SHell_ and offers additional fucntions, better syntax, more stability, and is the default you will use on most _Linux_ distrubtions today.
	-   **ksh** — The _Korn SHell_ is simply another variant, adding functionality on top of _sh_ and _Bash_. It handles some scripting syntax better, for example.
	-   **zsh** — _Z Shell_ is another extension of _Bash_, adding additional functionality and implementing some improvements. **This is the shell we are using in *ESA Kali***.

> **Instructor Note** &mdash;  We use `zsh`. `bash` and `.sh` also installed. `bash` defaults still present in the configs located at `~`. 

> **Instructor Note** &mdash; Making a small note to [[04 Environment#Variables | environment variables]] here and [[12 Processes and Monitoring#Programs and Processes | processes]]

#### Process and Programs

> **Instructor Note** &mdash; Make sure that students understand ***everything*** on *Linux* is a file.

- Every OS, *Linux* included, manages many tasks at the same time. 
	- On *Linux* they are called "processes" and each as a ***process id*** or ***pid***
- Process = program, whether FireFox or the `ls` command.
	- `ps -aux | grep "grep"`

#### Environment Variables

- The environment us full of variables
	- Some standard to the system/user
	- Some temporary/set by the user
- All variables can be used/referenced with a `$` and the variable name. 

> **Instructor Note** &mdash; More on this later...

> **Student Tip** &mdash; Did you know you can create your own variables? Simple type a word, number, or combination of both followed with an `=` a sign and the value you want to assign in. The variable must be one word (or connected with `_`'s), but the value can be any length. Just be sure to encase it in quotes. For example `myVar="Apples"`, then type `echo $myVar`

### Demo 1-1 - Shell Game

> **Instructor Note** &mdash;  Follow-along demonstration. Primary goal is to get them to use a shell, show the difference between them, and introduce briefly to features of the environment. 
> See command palate [[#P1D1]] 
> Concept's used but not covered deeply
>> [[04 Environment#Variables | environment variables]]
>> [[12 Processes and Monitoring#Programs and Processes | processes]]

Open a new terminal and show we are using `zsh`. Define `echo`. 

> **Student Tip** &mdash;  `echo` is a basic terminal command that prints the text that follows. It can be used in a variety of contexts, and in the following case, it is printing the contents of a variable. 

```Bash
# Show the users default shell
kali@linux:~$ echo $SHELL
# Show current running process
kali@linux:~$ echo $0
```

From `zsh` open `bash`, identify the current process, exit, then do again for `sh`.

```Bash
# Change to 'bash'
kali@linux:~$ bash
# Show current running process
kali@linux:~$ echo $0
```

> **Student Tip** &mdash; Why doesn't `grep` have any color in `bash`? This is due to the smart coloring for `zsh` and a really neat feature. All of this can be customized. 

```Bash
exit
# Back to `zsh`
kali@linux:~$ echo $0
# Change to 'sh' - Color is back!
kali@linux:~$ sh
# Show current running process
kali@linux:~$ echo $0
# Show the environment variable despite the current process
kali@linux:~$ echo $SHELL && echo $0
```

> See this link for more information &mdash; [linux - How does "echo $0" work? - Super User](https://superuser.com/questions/1445395/how-does-echo-0-work)

For some fun, see [[field_of_vars.sh]]

> **Student Tip** &mdash; What's the deal with `&&`? You can chain commands together on the command line to make things easier to read, simpler to copy and paste, or just easier to run. In this case we told the terminal to "print the variable **SHELL** to screen **and then** print the variable **0** to screen." You can also separate commands with `;` Try it!

> **Student Tip** &mdash; So why did the two variables print different values? Think back to processes. The main processes is `zsh`, the terminal we stated in. From there, we started another process inside the first one called `sh`. Changing the *current* shell changed the value of `$0`, but it didn't change `$SHELL`. *WHY?* Because the first is a variable specific to the process, the second is an ***[[04 Environment | environment variable]]*** that doesn't change unless explicitly told to.

### Demo 1-2 - Did you read the manual?

> **Instructor Note** &mdash; Short introduction to `man` pages. 

Every command has a corresponding *"manual"*, or `man`, page. You access a commands manual page with `man [COMMAND]`. 

```Bash
man echo
```

Basic `man` navigation. 
- `q` for quit
- `/` to enter search. <kbd>Enter</kbd> to find the nearest occurrence. Scroll away from the found instance and search again to find the next. 
- <kbd>Page Up</kbd> and <kbd>Page Down</kbd> are effective for navigating. 

> **Instructor Note** &mdash; Student question. **What is the current version of the `man` command?

```Bash
man man
# Find the version 2.9.4 at the bottom of the page. 
man --v
# Print version
```

# Part 2 - File System Navigation

> **Instructor Note** &mdash; Brief reminders on how the file system works and is structured. The only context required is that required to accomplish basic navigation and manipulation. 
> We will use the opportunity to talk about and use some of the top priority files like `/etc`. 

## Live-Lecture 2-1 - Navigating the FHS

 **Instructor Note** &mdash; This live a **live lecture**. Walk through the file system with students and explain the various pieces as you go. At each portion of the lecture, demonstrate the concepts on the command line. 

### The File System

> **Instructor Note** &mdash; Make sure students know that the terms *"directories"* and *"folders"* are interchangeable.

- *Linux* does not use drive letters like *Windows*
- Everything based on **root** or `/`, all other directories are a children of, and have a path from, root. 


### Part 1 - Basic Navigation

- `cd`
- `pwd`
- `ls`
- `file`

#### Paths

##### absolute

**_Absolute_** references refer to referencing a file or directory by starting with the root `/` directory. For example, to navigate to the `Documents` directory from anywhere on the system:

```bash
kali@linux:~$ cd /home/linux/Documents
```

For scripts, programs, configurations, etc., that rely on a specific directory and must eb able to run from anywhere, _absolute_ references are best.

##### relative

A **_relative_** reference is a file or directory reference "relative" to the current working directory. This works because of where you are in the system. From the users "home" directory, which is `/home/linux`, the file tree looks like this:

```bash
/home/linux
	/Documents
	/Downloads
	/Pictures
	/...
```

To move from `Documents` to `Downloads`, for example, use the syntax:

```bash
kali@linux:~$ cd ../Downloads
```

To reference a file in the `Downloads` directory, the syntax is similar:

```bash
kali@linux:~$ file ../Downloads/somefile.txt
```

The `~` symbol represents the user's home directory, `/home/linux`. You may use this in **_relative_** references. To navigate to `Documents` from anywhere, the syntax is:

```bash
kali@linux:~$ cd ~/Documents
```

##### Short Hand

There are also a few short-hand notes to keep in mind.
- You can refer to the current directory be adding `./` to the beginning of path.
- The shorthand for the directory above you is `../`, and can be used multiple times for multiple directories up.
- The users **home** directory (`/home/USER`) is also known as `~` and can used in a path. This is **relative to the current user**. 

## Demo 2-1  - Directory Shuffle

> **Instructor Note** &mdash; Students will navigate the file system using absolute and relative paths and some new binaries to learn where things are. We are also going to introduce [[04 Environment#Aliases | aliases]] with `l` and `ll`. As you change directories, note how the terminal prompt changes wit you and explain the `$` stands for a normal user, as does the blue color. 
> - See command palate [[#P2D1]]

Open a terminal and go over the three basics of navigation. 
1. Where am I (and what is here)
2. Swift easy, and accurate navigation (with tab completion when possible)
3. Where am I (and what is here)

### Going up

```Bash
# 1. Where am I (and what is here)
kali@linux:~kali@linux:~kali@linux:~kali@linux:~kali@linux:~$ pwd
# 2. Change up one directory
kali@linux:~$ cd ../
# 3. Where am I (and what is here)
kali@linux:~$ pwd
kali@linux:~$ ls
kali@linux:~$ ls -l
kali@linux:~$ ls -a
kali@linux:~$ ls -la
# "Aliases" for `ls` and `ls -la`
kali@linux:~$ l
kali@linux:~$ ll
```

> **Instructor Note** &mdash; Explain colorizing here and whenever a new color appears. 

#ST *Kali Linux* and other "shells" often use special colors for different items on the command line. In this shell, blue is for directories, and white is for files. There are other colors you will become familiar with. 

### Going down

```Bash
# 1. Where am I (and what is here)
kali@linux:~$ pwd
kali@linux:~$ ll
# 2. Change directory
kali@linux:~$ cd eddie/
# 3. Where am I (and what is here)
kali@linux:~$ pwd
# Recursively listing files
kali@linux:~$ ls -lR
```

#ST What's an [[04 Environment#Aliases | alias]]? You can set any set of characters to equal another. Often, *"aliases"* are used to turn longer commands that are used frequently into shorter ones, such as using `ll` instead of `ls -la`. It may seem silly, but it helps when you use the command line heavily.

### Relative Paths

> **Instructor Note** &mdash; Introducing tab-complete here

```Bash
kali@linux:~$ cd Documents/
# Changing to a directory one layer up relative to ours.
kali@linux:~$ cd ../Do # Tab-complete!
Completing directory
Documents/  Downloads/
kali@linux:~$ cd ../Dow # Tab-complete!
kali@linux:~$ cd ../Downloads
# Let's go higher!
kali@linux:~$ cd ../../../etc/apache2/
kali@linux:~$ pwd
kali@linux:~$ ls
# Head back to home
kali@linux:~$ cd ~
```

> **Instructor Note** &mdash; Stop and confirm understanding of what happened. 

### Absolute Paths

> **Instructor Note** &mdash; Much easier to understand. Taking the opportunity to explain that absolute paths are important when the context of relative paths may break depending on the user or scenario. 

```Bash
kali@linux:~$ ls
kali@linux:~$ cd /home/eddie/Documents
kali@linux:~$ pwd
kali@linux:~$ cd /var/log/apache2/
kali@linux:~$ cd 
kali@linux:~$ cd /home/eddie/Downloads
kali@linux:~$ cd /home/eddie/.config/chromium/Default
```

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


- `cat`
- `more`
- `less`
- `head`
- `tail`
- `touch`
- `rm`
- `mkdir`
- `mv`
- `cp`

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


## Lab Steps
1. Launch a terminal
2. `man` command
3. `man gr` with tab complete
	1. Explore `man grep`
4. `pwd`
5. `clear`
6. `cd /etc/apache`

> Begins dealing with errors by changing to the wrong directory.
> Begins dealing with `../`, *asbsolute/relative path*, and the *home* directory `~`. 

7. ls

> Begin ls

### File Manipulation

1. mkdir
2. `cp`
	1. Spend time detailing the portions of the command

![[Pasted image 20221025155733.png]]

3. `file`. 
4. `cat`
5. `touch`
6. `rm`