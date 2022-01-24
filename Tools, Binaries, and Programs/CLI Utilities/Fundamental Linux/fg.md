# Foreground (fg)
The `fg` command stands for "foreground" and we use it to bring commands running in the background to the foreground

See [Processes and Monitoring](../../../Knowledge%20Base/Linux%20Fundamentals/12%20Processes%20and%20Monitoring.md), [bg](bg.md), and [jobs](jobs.md) for more information. 
## Syntax

```
fg %[job number]
```

For example:
```
┌──(kali㉿kali)-[~]
└─$ jobs                                                        2 ⚙
[1]  - running    sudo tcpdump -i eth0 -w capture.pcap
[2]  + running    nmap -p- scanme.nmap.org

┌──(kali㉿kali)-[~]
└─$ fg %1                                                       1 
[1]  + running    sudo tcpdump -i eth0 -w capture.pcap
```

There are several ways to reference a job in the background. 

- `%Number` &mdash; Reference a job by its number
- `%String%` &mdash; Reference the beginning of the commands name, such as `&tcpdump`
- `%+ or %%` &mdash; References the current job
- `%-` &mdash; Refers to the previous job

You can send a running command to the background after it started by using <kbd>ctrl</lbd>+<kbd>Z</kbd>.

> Note that if there is only one job in the background, no reference is needed and `fg` alone will bring it back.