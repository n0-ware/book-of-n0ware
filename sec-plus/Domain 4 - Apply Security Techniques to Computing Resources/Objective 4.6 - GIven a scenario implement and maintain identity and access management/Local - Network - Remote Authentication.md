---
tags:
topic: "sec_iam"
subTopic: "authentication"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_authentication" 
cert: "Sec+"
---
# Local - Network - Remote Authentication
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Authentication Provider
- An essential component of an operating system.
- Responsible for authenticating users before granting access.
- Relies on cryptographic hashes for knowledge-based authentication.

## Knowledge-Based Authentication
- Passwords are stored as cryptographic hashes.
- User-entered password is converted into a hash and compared to the stored hash.
- Authentication is successful if the hashes match.

## Windows Authentication
- Complex architecture with three typical scenarios:
  1. **Windows Local Sign-In**:
     - LSASS compares credentials to a hash in the SAM database (part of the registry).
  2. **Windows Network Sign-In**:
     - LSASS can authenticate against Active Directory (AD) domain controllers.
     - Preferably uses Kerberos for network authentication, but legacy apps may use NTLM.
  3. **Remote Sign-In**:
     - Used when the user's device is not on the local network.
     - Authentication can occur over VPN, enterprise Wi-Fi, or web portal.
     - Secure protocols establish a connection between the client, remote access device, and authentication server.

## Linux Authentication
- Local user accounts stored in `/etc/passwd`.
- Passwords checked against hashes in `/etc/shadow` for local login.
- Interactive network login commonly achieved via Secure Shell (SSH).
- SSH allows cryptographic key-based authentication as an alternative to passwords.
- Pluggable Authentication Module (PAM):
  - Enables various authentication providers (e.g., smart-card login).
  - Supports authentication to network directory services.
