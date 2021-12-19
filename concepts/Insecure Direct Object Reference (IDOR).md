# Insecure Direct Object Reference (IDOR)

IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability. An [access control](access%20control.md) [vulnerability](vulnerability.md)] is when an attacker can gain access to information or actions not intended for them. An IDOR vulnerability can occur when a web server receives [user-supplied input](user-supplied%20input.md) to retrieve objects (files, data, documents), and too much [trust](trust.md) as been placed on that input data, and the web application does not [validate](validate.md) whether the user should, in fact, have access to the requested object.

#idor
#accesscontrol
#userinput