# Grep and Extended Grep
Grep and its cousin Extended Grep are used to match text strings to input, either from within a file or via a command piped into them. 

## Grep
`grep` us used to search text and files for a given string or[Regular Expressions (regex)](../../../Knowledge%20Base/Concepts/Regular%20Expressions%20(regex).md). 

### Usage

- `-r` &mdash; Recursive searching
- `-i` &mdash; Ignore case
- `-e` &mdash; Search with a regular expression
- `-v` &mdash; Invert match (show only items that don't match the string or regex)

For example, return your user from the `/etc/passwd` file. 

```
┌──(kali㉿kali)-[~/Documents/GitHub/book-of-n0ware]
└─$ cat /etc/passwd | grep kali
kali:x:1000:1000:Kali,,,:/home/kali:/usr/bin/zsh

┌──(kali㉿kali)-[~/Documents/GitHub/book-of-n0ware]
└─$ cat /etc/passwd | grep -i KALI
kali:x:1000:1000:Kali,,,:/home/kali:/usr/bin/zsh
```

Or, return only **not** your user from the file

```
┌──(kali㉿kali)-[~/Documents/GitHub/book-of-n0ware]
└─$ cat /etc/passwd | grep -v kali
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
...
Shortened
...
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
splunk:x:1001:1001:Splunk Server:/opt/splunk:/bin/bash
```

Or to search for a binary in `/usr/bin`
```
┌──(kali㉿kali)-[~/Documents/GitHub/book-of-n0ware]
└─$ ls /usr/bin/ | grep python
apython
dh_python3-ply
ipython3
pybabel-python3
python
python2
python2.7
python2.7-config
python2-config
python3
...
Shortened
...
```

## Egrep
### Usage
`egrep` is used when you intend to use an "extended [regular expression](../../../Knowledge%20Base/Concepts/Regular%20Expressions%20(regex).md)" beyond just a simple `string|otherstring` command via the `-E` flag with classic `grep`. It can be combined with other flags as well, and the [Regular Expressions (regex)](../../../Knowledge%20Base/Concepts/Regular%20Expressions%20(regex).md) is always wrapped in single quotes, such as `'^(linux|unix)'`.

### Arguements
- `-i` &mdash' Case insensitive pattern match
- `-W` &mdash; Matches whole words

### Regex

See [Regular Expressions (regex)](../../../Knowledge%20Base/Concepts/Regular%20Expressions%20(regex).md)


### Examples
***IP Matching***
```
egrep '[[:digit:]]{1,3}\.[[:digit:]]{1,3}\.[[:digit:]]{1,3}\.[[:digit:]]{1,3}' file
```
***Low Priv User Enumeration via /etc/passwd***
```
cat /etc/passwd | egrep "1[0-9]{3}"
```
***Users with /home directories***
```
cat /etc/passwd | egrep "*home*"
```