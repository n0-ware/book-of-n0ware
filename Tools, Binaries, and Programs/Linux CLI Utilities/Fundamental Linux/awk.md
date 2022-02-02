# Awk
## Description

The command `awk` actually represents an entire programming language built for processing text. It has found a home as a tool for extracting data from files and is very useful in writing reports. `awk` is extremely powerful, and learning the full functionality of `awk` will take some time and practice. 

## Arguments

All of the scripting in `awk` takes place within the ``' '``   after any flags. Each portion of the script is contained in curly braces, `{}` and separated by a semicolon, `;`. 
- `-F` &mdash; The "field" seperator
- `'{print $1, $2, $etc...}'` &mdash; Outputs the resulting text based on the associated field seperator. 
- `'BEGIN{ }'` &mdash' Begin rules are executed once before the first input record is read.
	- `ORS=` is a common rule and stands for `Output Records Separator and will replace the standard "new line" record separator with your choice. 
	- `OFS=` will replace the output field separator with something of your choosing. Commonly used with `-F`. 
- `'END { }'` &mdash; Conversely, End rules are executed at the end after all input is read


## Examples

***Strip fields from an AWS ARN.***

```
┌──(kali㉿kali)-[~]
└─$ echo "arn:partition:service:region:account-id:resource-type:resource-id" | awk -F ":" '{print $3, $5, $6, $7}'
service account-id resource-type resource-id
```

***Print last octet in an IP address list

```
┌──(kali㉿kali)-[~/Documents/GitHub]
└─$ cat ip_list.txt                         
192.168.1.2
192.168.1.187
192.168.1.89
192.168.1.76
192.168.1.254
192.168.1.269
192.168.1.78
192.168.1.177
192.168.1.198
192.168.1.73
192.168.1.5
192.168.1.9
                                                                                     
┌──(kali㉿kali)-[~/Documents/GitHub]
└─$ cat ip_list.txt | awk -F "." '{print $4}'
2
187
89
76
254
269
78
177
198
73
5
9
```

***Print the last octet, comma-separated***
```
┌──(kali㉿kali)-[~/Documents/GitHub]
└─$ cat ip_list.txt| awk -F "." 'BEGIN {ORS=" "}; {print $4}' 
2 187 89 76 254 269 78 177 198 73 5 9     
```

***Print the shell for all users in `/etc/passwd` replacing ":" with "="***
```
┌──(kali㉿kali)-[~/Documents/GitHub]
└─$ cat /etc/passwd | awk -F ":" 'BEGIN {OFS="="}; {print $1, $7}'
root=/usr/bin/zsh
daemon=/usr/sbin/nologin
bin=/usr/sbin/nologin
sys=/usr/sbin/nologin
sync=/bin/sync
games=/usr/sbin/nologin
man=/usr/sbin/nologin
...
Shortened
```

