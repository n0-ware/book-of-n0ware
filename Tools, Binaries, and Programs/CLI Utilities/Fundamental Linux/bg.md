# Background (bg)
## Description

Sending a command to the `background` allows us to manage [Processes](../../../Knowledge%20Base/Linux%20Fundamentals/12%20Processes%20and%20Monitoring.md#Processes) that may take some time to finish. 

Long-running programs are sent to the background by adding `&` to the end of the command. 

```
┌──(demouser㉿kali)-[~]
└─$ nmap -p- -sC scanme.nmap.org &                            130 ⨯
[1] 47596

Starting Nmap 7.92 ( https://nmap.org ) at 2022-01-20 21:18 EST
┌──(demouser㉿kali)-[~]
└─$ jobs                                                        
[1]  + running    nmap -p- -sC scanme.nmap.org
```

You can send a running command to the background after it started by using <kbd>ctrl</lbd>+<kbd>Z</kbd>.

See [jobs](jobs.md) and [fg](fg.md) for more information on managing jobs in the background and foreground. 