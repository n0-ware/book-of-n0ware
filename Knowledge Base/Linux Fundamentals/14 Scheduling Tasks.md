# Scheduling Tasks
In *Linux*, it is possible to schedule [jobs](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/jobs.md) to run at intervals, with various privileges, and to various purposes. These "jobs" can be simple or complex, from complex chains to simple copying of logs. The tool *Linux* uses as a "job-scheduler" is `Cron`.

## Cron

Scheduled tasks in *Linux* are generally known as "cron jobs." The `Cron` tool manages the scheduling and execution of system tasks, generally for system maintenance or other routine tasks. 

The tasks are stored in the `/etc/cron.*/` directories. The `*` represents the frequency of tasks, each stored in a different directory. Below is a listing of the various files and their frequency. 

```
┌──(kali㉿kali)-[/etc]
└─$ ls cron*
crontab

cron.d:
e2scrub_all  john  php  sysstat

cron.daily:
apache2  apt-compat  debtags  dpkg  google-chrome  logrotate  man-db  ntp  plocate  samba  sysstat

cron.hourly:

cron.monthly:
rwhod

cron.weekly:
man-db
```

The `crontab` file in the `/etc` directory is where additional scheduled tasks are often added by system administrators. This is often a source of compromise, as most of these scripts are ran as root with root privileges, and if not carefully inspected and protected, these commands can be insecure. Imagine a "cron job" scheduled here that writes to a configuration file using a custom binary file that is itself insecure. If the job runs as root, and the script it calls is editable, then the job is editable. 

```
┌──(kali㉿kali)-[/etc]
└─$ cat /etc/crontab               
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```

An example addition to the "crontab" to create a backup of the `/etc/passwd` directory may look like this. 

```
99 37 13 * * 3 root cp /etc/passwd /etc/passwd.bk
```
Specific user "crontabs" are often kept in the `/var/spool/cron/crontabs` directory and are another location to investigate from both the blue and red perspectives. 

Use the [crontab](../../Tools,%20Binaries,%20and%20Programs/Linux%20CLI%20Utilities/Fundamental%20Linux/crontab.md) command to view and edit a users crontab directly:

```
┌──(kali㉿kali)-[~]
└─$ crontab -u kali -e
```

