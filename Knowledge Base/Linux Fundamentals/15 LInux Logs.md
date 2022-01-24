# Linux Log Files
Nearly everything that happens on a system is either recoded by default or can be configured to record, in a log file. Security professionals and system administrators alike must become familiar with log files as a resource for managing the security of their systems, searching for information in logs, or even covering your tracks in a penetration testing engagement. 

Most logs cannot be read without *root* permissions, requiring [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) access for non-*root* users. 

### Types

Most log types can be grouped into four categories:
1. Application Logs
2. Event Logs
3. Service Logs
4. System Logs

The log files in *Linux* are stored in the `/var/log` directory, for both core system services and records as well as installed programs such as `apache2`.

```
┌──(root💀kali)-[/var/log]
└─# ls -l               
total 3044
-rw-r--r--  1 root              root             24156 Jan 23 18:21 alternatives.log
-rw-r--r--  1 root              root             12516 Dec 31 11:20 alternatives.log.1
-rw-r--r--  1 root              root              4337 Nov 29 21:19 alternatives.log.2.gz
-rw-r--r--  1 root              root               807 Oct  7 16:05 alternatives.log.3.gz
-rw-r--r--  1 root              root              2272 Sep 30 12:47 alternatives.log.4.gz
-rw-r--r--  1 root              root              1095 Jul 19  2021 alternatives.log.5.gz
-rw-r--r--  1 root              root              6453 May 30  2021 alternatives.log.6.gz
drwxr-x---  2 root              adm               4096 Jan 22 00:00 apache2
drwxr-xr-x  2 root              root              4096 Jan 23 18:21 apt
-rw-r-----  1 root              adm              39663 Jan 23 19:39 auth.log
-rw-r-----  1 root              adm              90285 Jan 22 23:59 auth.log.1
-rw-r-----  1 root              adm              14100 Jan 20 23:59 auth.log.2.gz
-rw-r-----  1 root              adm              17575 Jan 14 22:15 auth.log.3.gz
-rw-r-----  1 root              adm               1754 Jan  3 09:57 auth.log.4.gz
-rw-------  1 root              root                 0 Jan 21 00:00 boot.log
-rw-------  1 root              root              4201 Jan 21 00:00 boot.log.1
-rw-------  1 root              root               593 Jan 18 00:00 boot.log.2
-rw-------  1 root              root              4142 Jan 17 15:48 boot.log.3
...
```

Most of the logs are just text files, readable (and editable!) without any additional programs or resources, such as the `apache2` log `access.log`.

```
┌──(root💀kali)-[/var/log/apache2]
└─# cat access.log       
127.0.0.1 - - [23/Jan/2022:19:43:47 -0500] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [23/Jan/2022:19:43:48 -0500] "GET / HTTP/1.1" 200 3379 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [23/Jan/2022:19:43:50 -0500] "GET / HTTP/1.1" 200 3379 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [23/Jan/2022:19:43:54 -0500] "GET /index.html HTTP/1.1" 200 3379 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
```

Another example is the `syslog` file:

```
┌──(root💀kali)-[/var/log]
└─# tail syslog
Jan 23 19:25:01 kali CRON[40856]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jan 23 19:35:01 kali CRON[40912]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jan 23 19:39:01 kali CRON[40925]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Jan 23 19:39:01 kali systemd[1]: Starting Clean php session files...
Jan 23 19:39:01 kali systemd[1]: phpsessionclean.service: Deactivated successfully.
Jan 23 19:39:01 kali systemd[1]: Finished Clean php session files.
Jan 23 19:43:45 kali systemd[1]: Starting The Apache HTTP Server...
Jan 23 19:43:45 kali apachectl[41180]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Jan 23 19:43:45 kali systemd[1]: Started The Apache HTTP Server.
```

As you can see in the last line, the `Apache HTTP Server` was started at `19:43:45` and shortly after some access logs appeared in the first log at `19.43.47`. This directly correlates to the activity I took on the system. 

### Special

Some logs are special in that they do require a particular command to read.

#### who

 One such is the `wtmp` file, requiring the [who](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/who.md) command to read. 

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

#### journalctl

Another special log worth noting is the `journalctl` log. You may notice this log referenced when using the `systemctl` command if you encountered an error in the process of attempting to start a command. *systemd* (read more [here](https://en.wikipedia.org/wiki/Systemd)), stores many logs readable by `journalctl`. These are often related to [STDERR](07%20Redirecting%20Output.md#STDERR)/STDOUT, service message, syslog messages, and more. 

Alone, `journalctl` will simply list the log files starting with the beginning of the log file. This will create pages and pages of files.

```
journalctl [options]
```

**Arguments**
- `-utc` &mdash; Displays timestamps in `utc` format
- `-b [boot]` &mdash; Display logs from current boot or `[boot]` number or ID
- `--list-boots` &mdash; 
- `--since` &mdash; List logs from a date using `YYY-MM-DD HH:MM:SS` format. Alternatively, you can use strings such as `yesterday` or `"1 hour ago"`. 
- `--until` &mdash; Follows the same format above, often combined with `--since` 
- `-u [service]` &mdash; Filter by service of interest, such as `apache2` or `sshd` or `nginx.service`
- `_PID, _UID, _GID [id #]` &mdash; List by PID
- `-r` &mdash; View in reverse order (newest first) 
- `-f` &mdash; Print new entries as they come in, like [watch](../Fundamental%20Linux/watch.md) 
- And many more...

Below is another look at the `apache2` service starting as recorded by `journalctl`

```
┌──(root💀kali)-[/var/log]
└─# journalctl | tail                                                                                        141 ⨯
Jan 23 19:56:56 kali apachectl[41612]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Jan 23 19:56:56 kali systemd[1]: apache2.service: Deactivated successfully.
Jan 23 19:56:56 kali systemd[1]: Stopped The Apache HTTP Server.
Jan 23 19:57:03 kali systemd[1]: Starting The Apache HTTP Server...
Jan 23 19:57:03 kali apachectl[41627]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Jan 23 19:57:03 kali systemd[1]: Started The Apache HTTP Server.
Jan 23 19:57:23 kali systemd[1]: Stopping The Apache HTTP Server...
Jan 23 19:57:23 kali apachectl[41656]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
Jan 23 19:57:23 kali systemd[1]: apache2.service: Deactivated successfully.
Jan 23 19:57:23 kali systemd[1]: Stopped The Apache HTTP Server.
```

You can filter the output of `journalctl` with the `-u [service]` flag, and they are visible in reverse order (new first) with the `-r` flag. You can monitor `journalctl` in a similar way to [watch](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/watch.md) with the `-f` flag. 

#### dmesg

Kernel logs, often complex and only of interest to the operations of the kernel, are viewed with `dmesg`. 


Some great information on *Linux* logs can be found in more detail [here](https://stackify.com/linux-logs/). 

