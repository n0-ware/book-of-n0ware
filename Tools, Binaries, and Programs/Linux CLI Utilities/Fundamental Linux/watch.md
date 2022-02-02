# watch
## Description

Often, we may want to run a command at regular intervals, such as an export, copy, backup, etc. The `watch` command is used to do this. The default interval for `watch` to run a command is every two seconds, but this can be changed. 

## Syntax

```
watch [options] [command]
```

The `-n` flag is used to set the interval you want for `watch`. For example, if I was writing a `tcpdump` capture file and wanted to copy that file to a new location, it would look like this. 

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