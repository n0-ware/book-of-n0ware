# jobs

## Description

The `jobs` command is used to view the running jobs or [processes](../../../Knowledge%20Base/Linux%20Fundamentals/12%20Processes%20and%20Monitoring.md#Processes) in the background

```
┌──(kali㉿kali)-[~]
└─$ jobs                                                        2 ⚙
[1]  - running    sudo tcpdump -i eth0 -w capture.pcap
[2]  + running    nmap -p- scanme.nmap.org
```

See [fg](fg.md) and [bg](bg.md) for more information on bringing commands back from, or sending them to, the "foreground" and "background."