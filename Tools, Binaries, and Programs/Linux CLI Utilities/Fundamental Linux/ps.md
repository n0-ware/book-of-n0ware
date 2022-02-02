# Process Status (ps)
## Description

The `ps` command is used to view the process's status. There are several useful ways to filter this command, such as `-ax` for all processes running. Or, `-U` for the user and `-u` for the effective user, such as `ps -U root -u root` to view all processes running as root or effectively as root, and more. 

A common use of `ps` is to pipe it with grep to search for specific process names

```
ps -aux | grep [process name]
```

This is great for defenders and attackers alike searching for running processes by name, such as `apache`, `nginx`, and so on. 

`ps` is so well known among Unix-like operating systems and others that even Windows recognizes it as a built-in command with essentially the same purpose. 

References:
- [Processes](../../../Knowledge%20Base/Linux%20Fundamentals/12%20Processes%20and%20Monitoring.md)
- [jobs](jobs.md)
- [fg](fg.md)
- [bg](bg.md)

## Syntax

```
ps [options]
```

Some of the more important fields of `ps` are

 **UID** &mdash; User ID
- **PID** &mdash; Process ID
- **PPID** &mdash; Parent Process ID
- **Time** &mdash; Time running
- **CMD** &mdash; Command name


**Arguments**
- `-e or -A` &mdash; List all processes
-  `-a` &mdash; List all processes, ike `-A`, but skip those not associated with a terminal. 
- `-f` &mdash; List in full file format
- `-C [command name]` &mdash; Select by command name
- `-U [username]` &mdash; Select by **real** user ID (RUID)
- `-u [username]` &mdash; Select by **effective** user ID (EUID)
- `-x` &mdash; Print all processes owned by user `x`. 

## Examples

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

## Examples

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

## Useful

Print all processed owned, effectively or real, by `root`
```
ps -U root -u root
```