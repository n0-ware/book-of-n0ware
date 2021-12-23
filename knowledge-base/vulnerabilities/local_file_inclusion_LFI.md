# Local File Inclusion

Tags [^1]

[^1]: #webapp #lfi #get #post #query #insecuredesign 
## Description
Local File Inclusion (LFI) vulnerabilities can be found in web applications. **LFI** allows attackers to "include" and read local files on the server, such as cryptographic keys, passwords, API's, and other sensitive data. **LFI** can result in sensitive data exposure, a former [*Owasp Top Ten*](https://owasp.org/www-project-top-ten/) vulnerability, now included in the number two spot with [*Cryptographic Failures*](cryptographic_failures.md)

This type of vulnerability occurs when developer's lack security awareness and instead focus solely on convenience. Developers need to read local files within a specific page, on occasion. If they include those files without the right input validation, an **LFI** vulnerability exists as an attacker can call the file with malicious [user-supplied input](../concepts/user_supplied_input.md)

Once discovered, if the file has the right permissions, the attacker can read the file. This can include both files sensitive to the application **and** files holding sensitive user information. 

Further, if we can inject or write to a file on the system, we can use **LFI** to obtain [**remote code execution (RCE)**](remote_code_execution_rce.md).
## Finding

### HTTP Query Parameters
This is the attackers main point of interest to see if they can manipulate the parameters of an `HTTP` [query](../concepts/queries.md) to input and inject attack payloads and see how the application responds and find an entry point. Often these are `HTTP` [GET](../concepts/web/GET.md) and [POST](../concepts/web/POST.md) parameters that pass arguments and data to a web app to perform a specific operation. 

![HTTP Query Parameters](../concepts/concepts_photos/HTTP_Query_Parameters.png)

Once an entry point for potential **LFI** is identified, you need to understand how the data could be processed inside the application. Once found, specific testing for vulnerability types begins manually or with automation. 

*Below is some `PHP` that is vulnerable to **LFI***

```
<?PHP
	include($_GET["some_file"]);
?>
```

This code uses a `GET` request via the URL parameter `file` to include that file on the page. Sending an HTTP request that mirrors this `PHP` code could load the content of any file, such as `welcome.txt`, as long as the file is available in that directory.

`http://vulnsite.io/index.php?file=welcome.txt`

> In `PHP` code, the following functions cause this type of vulnerability
> - `include`
> - `require`
> - `include_once`
> - `require_once`

There are many entry points, others including &mdash; User-Agent, Cookies, session, and other HTTP headers. 

*Valuable files to try and read include:*
- `/etc/shadow`
- `/etc/passwd`
- `/etc/issue`
- `/etc/group`
- `/etc/hosts`
- `/etc/motd`
- `/etc/mysql/my.cnf`
- `/proc/[0-9]*/fd/[0-9]*`  (first number is the PID, second is the file descriptor)
- `/proc/self/environ`
- `/proc/version`
- `/proc/cmdline`

## Examples

