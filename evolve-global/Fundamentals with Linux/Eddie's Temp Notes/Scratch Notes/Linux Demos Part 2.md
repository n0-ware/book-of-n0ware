# Part 2 - File System Navigation

> **Instructor Note** &mdash; Brief reminders on how the file system works and is structured. The only context required is that required to accomplish basic navigation and manipulation. 
> We will use the opportunity to talk about and use some of the top priority files like `/etc`. 
> Command palate 

## Live-Lecture 2-1 - Navigating the FHS

> **Instructor Note** &mdash; This live a **live lecture**. Walk through the file system with students and explain the various pieces as you go. At each portion of the lecture, demonstrate the concepts on the command line. 

### The File System

> **Instructor Note** &mdash; Make sure students know that the terms *"directories"* and *"folders"* are interchangeable.

![[0.5 Basic Linux Usage#The File System <a id="file-system"></a>]]

### Navigation Basics

#### Basic Commands

##### Change Directory - cd

![[01 Navigation#cd]]

##### Print Working Directory - pwd 

![[01 Navigation#pwd]]

##### Listing Files - ls

> **Instructor Note** &mdash; Introduce the concept of hidden files.

![[02 Listing Files#ls]]

##### File Information - file

![[01 Navigation#file]]

#### Paths

> **Instructor Note** &mdash; Take the opportunity to demonstrate using the paths.

Linux has simple rules for the file using and navigating the file system
- Everything starts with the system root at `/`.
- Each section is often referred to as  a *"layer"* or *"level"* 
- The location of a file is known as its ***"path"***
- A path can be either absolute or relative, and either can be used when referencing a file or folder
![[01 Navigation#absolute | absolute]] 

or 

![[01 Navigation#relative | relative]]

There are also a few short-hand notes to keep in mind.
- You can refer to the current directory be adding `./` to the beginning of path.
- The shorthand for the directory above you is `../`, and can be used multiple times for multiple directories up.
- The users **home** directory (`/home/USER`) is also known as `~` and can used in a path. This is **relative to the current user**. 

### FHS

> **Instructor Note** &mdash; Navigate the **FHS** using shorthand when possible. 

> Navigate to and explain the following directories &mdash; etc, bin, mnt/mount, opt, var, usr. Keep high level.

![[0.5 Basic Linux Usage#Filesystem Hierarchy Standard (FHS) <a id="fhs"></a>]]


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

## Command Palates

### P2D1

```Bash
# 1. Where am I (and what is here)
kali@linux:~$ pwd
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
# 1. Where am I (and what is here)
kali@linux:~$ pwd
kali@linux:~$ ll
# 2. Change directory
kali@linux:~$ cd eddie/
# 3. Where am I (and what is here)
kali@linux:~$ pwd
# Recursively listing files
kali@linux:~$ ls -lR
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
kali@linux:~$ ls
kali@linux:~$ cd /home/eddie/Documents
kali@linux:~$ pwd
kali@linux:~$ cd /var/log/apache2/
kali@linux:~$ cd 
kali@linux:~$ cd /home/eddie/Downloads
kali@linux:~$ cd /home/eddie/.config/chromium/Default
```