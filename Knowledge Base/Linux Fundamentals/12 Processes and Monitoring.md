# Processes

## Table of Contents

###### Tags[^2]

[^1]:https://en.wikipedia.org/wiki/Job_control_(Unix)
[^2]:#fundamentals #linux #processes 

- [Jobs](#Jobs)
	- [Background](#Background)
	- [Foreground](#Foreground)
	- [Status](#Status)
	- [Kill](#Kill)
- [Monitoring](#Monitoring)
	- [Tail](#Tail)
	- [Watch](#Watch)




## Programs and Processes

Like most computer systems, the operating system is capable of managing an astounding amount of tasks at the same time. The *Linux* kernel is no exception, and it manages all of these tasks by using *processes*. 

A *process* is can be thought of as a program. From something as complex and persistent as a web browser to the brief occurrence of `cd` or `ls`, every process that runs on a *Linux* machine is a program, and each command is considered its own program, and therefore its own process. 

To keep things organized, and so users can reference the various processes on the sytem, each gets a unique identifier called the ***process id***. 


## Jobs

To further compartmentalize and organize things, *Linux* uses the concept of ***jobs*** to manage workflow on the terminal. For example, if we run the command `cat file.txt | grep sometext`, we have two commands forming a single *job*. This example is a very quick job. With job control[^1], users can manage jobs in both the foreground and the background when the user wants to have a job persist for more than the time it takes to `cat` and `pipe` a file into `grep`. Utilities such as `tcpdump`, which captures packets, might need to run in the background or be suspended and resumed later. 

### Background

Jobs currently running on the terminal in view of the user are considered in the **foreground**. This prevents any other commands from running on the terminal until that one finishes. While most commands finish rapidly, as stated with `tcpdump`, this is not the case. The easiest way to background a process is to finish the command with the `&` symbol. 

Let's use `nmap` as an example. Running a slow and/or thorough `nmap` may take some time. The command below sends the command to the background. 

```
┌──(demouser㉿kali)-[~]
└─$ nmap -p- -sC scanme.nmap.org &                            130 ⨯
[1] 47596

Starting Nmap 7.92 ( https://nmap.org ) at 2022-01-20 21:18 EST
┌──(demouser㉿kali)-[~]
└─$ jobs                                                        
[1]  + running    nmap -p- -sC scanme.nmap.org
```

[Nmap](../../Tools,%20Binaries,%20and%20Programs/Information%20Gathering/Network%20Reconnaissance/Nmap.md) will now run in the background until it completes. 

Another example, reviewing the `tcpdump` situation, is running a packet capture in the background. 

```
┌──(kali㉿kali)-[~]
└─$ sudo tcpdump -i eth0 -w capture.pcap &
[1] 47851
                                                                    
┌──(kali㉿kali)-[~]
└─$ tcpdump: listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

┌──(kali㉿kali)-[~]
└─$ jobs                                                        1 ⚙
[1]  + running    sudo tcpdump -i eth0 -w capture.pcap
```

The [jobs](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/jobs.md) command allows us view the commands that are currently running. 

```
┌──(kali㉿kali)-[~]
└─$ jobs                                                        2 ⚙
[1]  - running    sudo tcpdump -i eth0 -w capture.pcap
[2]  + running    nmap -p- scanme.nmap.org
```

### Foreground

To bring a command back from the "background", we use the [fg](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/fg.md) command to bring a job back into the "foreground." Commands are terminated with the terminal shortcut <kbd>ctrl</kbd>+<kbd>c</kbd>.

Pairing the `fg` command with the number of the job you want to bring back is how we manage this. For example, to bring back the `tcpdump` command above, we use:

```
┌──(kali㉿kali)-[~]
└─$ fg %1                                                       1 
[1]  + running    sudo tcpdump -i eth0 -w capture.pcap
```

See [fg](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/fg.md) for more information and syntax on the "foreground" command. In short, there are multiple ways to bring commands to the foreground, including by the name or order of jobs. 

### Status

There are a lot of processes going on at once in a *Linux* system. Two of the ways you can manage them are with the `ps` command and `top` command. While [top](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/top.md) is mostly used for viewing processes by the system resources they consume, `ps` is more useful for viewing the processes in an organized fashion. We are going to discuss `ps` here. 

[ps](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/ps.md) stands for *process status* and has a great deal of complexity built into it. In short, it can be used for viewing a system-wide list of running processes, easily categorized by user, name, threads, and so on. 

Some of the more important fields of `ps` are

- **UID** &mdash; User ID
- **PID** &mdash; Process ID
- **PPID** &mdash; Parent Process ID
- **Time** &mdash; Time running
- **CMD** &mdash; Command name

Below uses the `-ef` flags, for selecting all processes (using `e`) and listing the full format. of columns (with `f`)
```
┌──(kali㉿kali)-[~]
└─$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 Jan17 ?        00:00:07 /sbin/init splash
root           2       0  0 Jan17 ?        00:00:00 [kthreadd]
root           3       2  0 Jan17 ?        00:00:00 [rcu_gp]
root           4       2  0 Jan17 ?        00:00:00 [rcu_par_gp]
root           6       2  0 Jan17 ?        00:00:00 [kworker/0:0H-events
root           9       2  0 Jan17 ?        00:00:00 [mm_percpu_wq]
root          10       2  0 Jan17 ?        00:00:00 [rcu_tasks_rude_]
root          11       2  0 Jan17 ?        00:00:00 [rcu_tasks_trace]
root          12       2  0 Jan17 ?        00:00:00 [ksoftirqd/0]
root          13       2  0 Jan17 ?        00:00:11 [rcu_sched]
root          14       2  0 Jan17 ?        00:00:01 [migration/0]
```
``

There is a lot of noise here. It may be easier to use either `grep` or the `-C` flag to filter for a command. With `nano` running, we can see this in action. 

```
┌──(kali㉿kali)-[~]
└─$ ps -fC nano
UID          PID    PPID  C STIME TTY          TIME CMD
kali       48133   39369  0 21:59 pts/3    00:00:00 nano
```

Or, using `grep`

```
┌──(kali㉿kali)-[~]
└─$ ps -ef | grep nano 
kali       48133   39369  0 21:59 pts/3    00:00:00 nano
kali       48366   42093  0 22:16 pts/4    00:00:00 grep --color=auto nano
```

Note that in the second situation, `grep` showed up because we used it to search for `nano`. 

### Kill

The `kill` command ends a process. There are a variety of flags and options that can be used. Two common ones are:

- `kill -9 PID` &mdash; Kills a process fully by its PID
- `killall [process name]` &mdash; Kills all processes associated with a process name

## Monitoring

A useful command-line feature is the ability to monitor files and commands in real-time. This is great on both the blue and red sides of the field, for monitoring sensitive logs, configuration files, etc. 

### Tail

The [tail](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/tail.md) command is used to monitor files, often displaying the updated contents as it changes with `tail -f`. Below, I started a local `apache2` server and accessed it over `localhost`. 

```
┌──(root💀kali)-[/var/log/apache2]
└─# tail -f access.log        
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://127.0.0.1/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET /favicon.ico HTTP/1.1" 404 487 "http://127.0.0.1/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
```

There are other flags available to change its functionality available on the `man` page or at [tail](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/tail.md). 

### Watch

The [watch](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/watch.md) command is used to set commands that run at regular intervals. While the default is every 2 seconds, this can be changed with the `-n` flag. 

For example, to set `cp` to run every 5 seconds to copy a `tcpdump` capture file as a backup, we use the syntax below. 

```
┌──(kali㉿kali)-[~]
└─$ sudo tcpdump -i eth0 -w capture.pcap &
[1] 5979
    
┌──(kali㉿kali)-[~]
└─$ tcpdump: listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes                     
    
┌──(kali㉿kali)-[~]
└─$ watch -n 5 cp capture.pcap capture.pcap.bk                             
┌──(kali㉿kali)-[~]
└─$ watch -n 5 cp capture.pcap capture.pcap.bk &
[2] 6034    
[2]  + suspended (tty output)  watch -n 5 cp capture.pcap capture.pcap.bk

┌──(kali㉿kali)-[~]
└─$ ls -l
-rw-r--r-- 1 tcpdump tcpdump 16384 Jan 21 09:41 capture.pcap
-rw-r--r-- 1 kali    kali    12288 Jan 21 09:41 capture.pcap.bk
```

First, we ran `tcpdump` to capture on `eth0` and write to `capture.pcap`.  Then we started `watch` in the background to copy `capture.pcap` to `capture.pcap.bk` every 5 seconds. You can see that watch already created the file via the `ls` in the last command. 
