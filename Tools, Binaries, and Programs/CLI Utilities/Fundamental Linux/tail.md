# tail
The `tail` command is used to monitor files. For example, monitoring log files as they are being written to. For example, we are attempting to launch a [Log Poisoning](../../../Knowledge%20Base/Vulnerabilities/Log%20Poisoning.md) attack, and have a presence on the server, we could use `tail` to monitor the logs for our poisoned code. 

## Syntax

```
tail [options] file
```

The default number of lines `tail` displays is `10`, but this can be changed. 

**Arguments**
- `-f` &mdash; Appends data to the output as the file grows
- `-n#` &mdash; Changes the default number of displayed lines to `#`
- `--pid [PID]` &mdash; Used in combination with `f` to terminate the `tail` process after the PID specified dies
- `-v` &mdash; Verbose output

## Example

```
┌──(root💀kali)-[/var/log/apache2]
└─# tail -f access.log        
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://127.0.0.1/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
127.0.0.1 - - [21/Jan/2022:09:26:09 -0500] "GET /favicon.ico HTTP/1.1" 404 487 "http://127.0.0.1/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36"
```

In this example, we are "following" the `access.log` file relating to an *Apache* webserver. Here, I accessed it over localhost, and you can see the activity it stored. 