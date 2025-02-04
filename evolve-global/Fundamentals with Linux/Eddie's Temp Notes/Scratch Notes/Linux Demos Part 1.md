# Part 0 - Virtualization

- [ ] Add task here

# Part 1 - Linux and Terminals
## Lecture 1-1 - Linux Basics

> **Instructor Note** &mdash;  Prepare a regular terminal, bash terminal, and `sh` terminal. 

### The Command Line

![[00 Linux Fundamentals#Using Linux <a id="using"></a>#The Command Line <a id="cli"></a>#]]

### Shells

![[00 Linux Fundamentals#Using Linux <a id="using"></a>#Shells]]

> **Instructor Note** &mdash;  We use `zsh`. `bash` and `.sh` also installed. `bash` defaults still present in the configs located at `~`. 

> **Instructor Note** &mdash; Making a small note to [[04 Environment#Variables | environment variables]] here and [[12 Processes and Monitoring#Programs and Processes | processes]]

### Process and Programs

> **Instructor Note** &mdash; Make sure that students understand ***everything*** on *Linux* is a file.

![[12 Processes and Monitoring#Programs and Processes]]

> **Instructor Note** &mdash; More on this laster...
### Environment Variables

![[04 Environment#Environment Variables#Definition]]

When we start a terminal from the desktop, or connect to our user remotely, the environment variable `$SHELL` determines the default shell for our user. 

> See this link for more information &mdash; [linux - How does "echo $0" work? - Super User](https://superuser.com/questions/1445395/how-does-echo-0-work)

> **Instructor Note** &mdash; More on this later...

> **Student Tip** &mdash; Did you know you can create your own variables? Simple type a word, number, or combination of both followed with an `=` a sign and the value you want to assign in. The variable must be one word (or connected with `_`'s), but the value can be any length. Just be sure to encase it in quotes. For example `myVar="Apples"`, then type `echo $myVar`

## Demo 1-1 - Shell Game

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

For some fun, see [[field_of_vars.sh]]

> **Student Tip** &mdash; What's the deal with `&&`? You can chain commands together on the command line to make things easier to read, simpler to copy and paste, or just easier to run. In this case we told the terminal to "print the variable **SHELL** to screen **and then** print the variable **0** to screen." You can also separate commands with `;` Try it!

> **Student Tip** &mdash; So why did the two variables print different values? Think back to processes. The main processes is `zsh`, the terminal we stated in. From there, we started another process inside the first one called `sh`. Changing the *current* shell changed the value of `$0`, but it didn't change `$SHELL`. *WHY?* Because the first is a variable specific to the process, the second is an ***[[04 Environment | environment variable]]*** that doesn't change unless explicitly told to.

## Demo 1-2 - Did you read the manual?

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

## Command Palates

### P1D1

```Bash
# Show the current shell
echo $SHELL
# Show current running process
echo $0
exit
# Back to `zsh`
echo $0
# Change to 'bash'
bash
# Show current running process
echo $0
exit
# Change to 'sh'
sh
# Show current running process
echo $0
# Show the environment variable despite the current process
echo $SHELL && echo $0
```