---
tags:
topic: "sec_code"
subTopic: "sdlc"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_sdlc" 
cert: "Sec+"
---
# Secure Coding Techniquees
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Security Considerations in Development

- Importance of understanding security in new programming technologies before deployment.
- Pressure to release often overlooks security considerations.
- Modern practices integrate a security development lifecycle (e.g., Microsoft's SDL, OWASP SAMM).

## Input Validation

- Essential technique addressing untrusted input.
- Prevents injection attacks (SQL injection, XSS, etc.).
- Methods include allowlisting, blocklisting, data type checks, range checks, and regular expressions.

## Secure Cookies

- Prevent attacks like session hijacking or XSS.
- Use 'Secure', 'HttpOnly', and 'SameSite' attributes.
- Set expiration time limits.

## Static Code Analysis

- Identifies vulnerabilities and errors early in development.
- Tools: SonarQube, Coverity, Fortify.
- Improves code quality and educates developers on secure practices.

## Code Signing

- Verifies code integrity and publisher's identity.
- Uses digital signatures and certificates from trusted CAs.
- Does not assure code safety or absence of vulnerabilities.

## Key Takeaways

- Secure coding is crucial for preventing common vulnerabilities.
- Practices include input validation, secure cookie handling, static code analysis, and code signing.
- Tools and methodologies support these practices to enhance software security.
