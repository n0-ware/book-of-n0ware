# Insecure Direct Object Reference (IDOR)
###### Tags[^1]
IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability. An [access control](definitions/access%20control.md)(access%20control.md) [vulnerability](definitions/vulnerability.md) is when an attacker can gain access to information or actions not intended for them. An IDOR vulnerability can occur when a web server receives [user-supplied input](definitions/user-supplied%20input.md)to retrieve objects (files, data, documents), and too much [trust](definitions/trust.md) as been placed on that input data, and the web application does not [validate](definitions/validate.md) whether the user should, in fact, have access to the requested object.

**TL;DR:** 

Change user supplied data to get access you should not have

## Vulnerability


### Finding

*Three places*
- [query](query.md) component

[^1]: #idor #accesscontrol #userinput #query 