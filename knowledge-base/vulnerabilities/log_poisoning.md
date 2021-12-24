# Log Poisoning

<u>***Refs***</u>
[Local File Inclusion](local_file_inclusion_LFI.md)

## Description

**Log Poisoning** refers to an attack where an applications log files manipulated to produce a negative result. Typically, the log is injected with malicious code that can do anything from divulge information to producing  [remote code execution](remote_code_execution_rce.md) depending on the type of [user supplied input](../concepts/user_supplied_input.md) we can inject into the log. 

***This attack has two prerequisites to be effective::**

1. We have ability to inject a malicious payload into a services log files, such as *Apache*  or *SSH*. 
2. We have access to the log file, either directly or via some other vulnerability such as [local file inclusion (LFI)](local_file_inclusion_LFI.md), so we may view the executed code and/or add to the corrupted log file with more code.  the we access the vulnerability is used to call the injected log file, executing the malicious payload. 

The prerequisites mean we need good enumeration and proof of concept skills beforehand to identify the vulnerability. It also requires some knowledge of how web applications work, such as when code is executed on the server-side and how that effects what we see on the client-side.

## Testing

Once you have determined you can view an applications log files, testing what you can control in the log file is the first step. 

For example, a log that captures the `User-Agent` field may be vulnerable to [injection](injection.md) through a modified `User-Agent` field. Attackers can modify a `curl` command to submits a custom `User-Agent` field with the `-A` flag.  This custom field can contain a payload, sent via `HTTP` request with `curl`. An *Apache* server will then attempt to read the log file, potentially executing any code you submitted. 

`curl -A "Testing for RCE" https://vulnsite.io/index.html`

Following the `curl` request, we then verify the custom `User-Agent` field was recorded and confirm the vulnerability. 

> `curl` has a bit of a learning code, but it allows you to entirely customize an `HTTP` request. 

If you are attacking `SSH`, this can be done via the username. Both require poor [user input](../concepts/user_supplied_input.md) sanitation. 

Once the malicious log is captured, we simply need to be able to access the log file to run the script. 

## Exploiting

### PHP
We identify a log that stores four headers &mdash; username, IP address, `User-Agent`, and the page visited

Since we can control the `User-Agent` field when interacting with a web application, we send a custom request to the web application on a page we know is logged. 

`curl -A "Testing for RCE" https://vulnsite.io/index.php`

We then inspect the log file to see if the custom `User-Agent` was recorded in the log. 

Next we send a "proof of concept" request injected with `PHP` code to see how the server/client renders the code. 
 
 `curl -A "<?php phpinfo()?>" https://www.vulnsite.io/index.php`
 
 Depending on how you access the log file, you will either see no `User-Agent` or the code will render information on the `PHP` backend. This is proof of [RCE](remote_code_execution_rce.md) and you may continue to exploit the service, whether through additional information disclosure or full compromise. 

