# Log Poisoning

## Description

*Referenced in [local_file_inclusion_LFI](local_file_inclusion_LFI.md) under Remote Code Execution*

**LFI** can be used to generate [remote code execution](remote_code_execution_rce.md) depending on the type of files we have access to. 

In the case of log files, this is called log poisoning, a technique used to gain **RCE** on a web server. The attack needs a malicious payload injected into a services log files, such as *Apache, SSH*, or others. Once there, the **LFI** vulnerability is used to call the injected log file, executing the malicious payload. This vulnerability requires multiple variables to align, meaning we need good enumeration beforehand to identify the vulnerability. It also requires some knowledge of how web applications work. 

For example, a user that can include a malicious payload in an Apache log file via a `User-Agent` header sent via an `HTTP` request. Via `SSH`, this can be done via the username. Both require poor [user input](../concepts/user_supplied_input.md) sanitation. 

Once the malicious log is captured, we simply need to be able to access the log file to run the script. 

Let's say we can access a log file, and we are able to pull a log that tells us precisely what the log stores. We identify that the log stores four headers &mdash; username, IP address, `User-Agent`, and the page visited. 

Attackers can control the `User-Agent` field when interacting with a web application, editing it with a crafted `HTTP` request using the `curl` command with the `-A` flag. Since we can control what `User-Agent` is sent to the log file, sending a test to the web application allows us to confirm if it works

> `curl` has a bit of a learning code, but it allows you to entirely customize an `HTTP` request. 

`curl -A "Testing for RCE" https://vulnsite.io/login.php`
## Finding

## Examples
