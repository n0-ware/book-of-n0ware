# who
The `who` command is a simple command used to report which users are currently logged in on a *Linux* system. 

```
┌──(root💀kali)-[/var/log]
└─# who
kali     tty7         2022-01-20 22:33 (:0)
kali     pts/1        2022-01-20 22:38
kali     pts/2        2022-01-20 22:38
kali     pts/5        2022-01-23 19:39
kali     pts/3        2022-01-21 09:40
```

The `who` command can also be used to read the `/var/log/wtmp` log file. 

```
┌──(root💀kali)-[/var/log]
└─# who wtmp 
kali     tty7         2021-05-31 03:34 (:0)
kali     tty7         2021-06-01 01:58 (:0)
kali     tty7         2021-06-28 15:14 (:0)
kali     tty7         2021-07-19 20:18 (:0)
kali     tty7         2021-07-19 21:31 (:0)
kali     tty7         2021-07-19 22:00 (:0)
kali     tty7         2021-07-20 09:44 (:0)
kali     tty7         2021-07-20 20:30 (:0)
kali     tty7         2021-09-11 23:45 (:0)
kali     tty7         2021-09-14 14:55 (:0)
kali     tty7         2021-09-30 12:38 (:0)
kali     tty7         2021-10-06 09:10 (:0)
...
```