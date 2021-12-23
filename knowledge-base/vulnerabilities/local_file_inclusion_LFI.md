# Local File Inclusion

Tags [^1]

[^1]: #webapp #lfi 
## Description
Local File Inclusion (LFI) vulnerabilities can be found in web applications. **LFI** allows attackers to "include" and read local files on the server, such as cryptographic keys, passwords, API's, and other sensitive data. **LFI** can result in sensitive data exposure, a former [*Owasp Top Ten*](https://owasp.org/www-project-top-ten/) vulnerability, now included in the number two spot with [*Cryptographic Failures*](cryptographic_failures.md)

This type of vulnerability occurs when developer's lack security awareness and instead focus solely on convenience. 

## Finding
In `PHP` code, the following functions cause this type of vulnerability
- `include`
- `require`
- `include_once`
- `require_once`

## Examples
