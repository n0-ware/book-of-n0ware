---
tags:
topic: "sec_wireless"
subTopic: "wireless_auth"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_wireless_auth" 
cert: "Sec+"
---
# Wirelss Authentication Methods
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# WI-FI AUTHENTICATION METHODS

## Personal Authentication
### WPA2 Pre-Shared Key (PSK) Authentication
- **Mechanism**: Uses a passphrase to generate a key for encrypting communications.
- **Configuration**: Passphrase of 8 to 63 ASCII characters, converted into a 256-bit HMAC.
- **Security**: Vulnerable to dictionary or brute force attacks; passphrase should be at least 14 characters long.

### WPA3 Personal Authentication
- **Improvement**: Uses Password-Authenticated Key Exchange (PAKE) with Simultaneous Authentication of Equals (SAE) protocol.
- **Security**: Prevents attackers from using offline brute force or dictionary attacks to recover the password.
- **Features**: Implements ephemeral session keys providing forward secrecy.

## Open Authentication
- Not explicitly detailed, but implies no encryption or use of a shared key, leaving data potentially exposed.

## Enterprise Authentication
- **Components**: Includes 802.1x authentication, RADIUS server, and unique user credentials.
- **Protocols**: Supports multiple Extensible Authentication Protocol (EAP) types like EAP-TLS, EAP-TTLS, and PEAP.
- **Dynamic Encryption Key Management**: Automatically changes encryption keys during a session.

## Remote Authentication Dial-In User Service (RADIUS)
- **Function**: A standard protocol for authenticating, authorizing, and accounting network access.
- **Workflow**:
  1. User device connects to Network Access Server (NAS) device.
  2. NAS prompts for authentication credentials.
  3. Credentials submitted as EAPoL data.
  4. RADIUS client (NAS) sends Access-Request to AAA server.
  5. AAA server responds with Access-Accept or Access-Reject.
- **Accounting**: Optional RADIUS function for logging, using port 1813.

## Considerations
- **Configuration Labels**: Access points may label authentication methods as WPA2-Personal, WPA3-SAE, or WPA3-Personal Transition mode.
- **Vulnerabilities and Security Updates**: Ongoing research and updates are essential to address flaws, such as downgrade attacks in WPA3-Personal.

Wi-Fi authentication methods play a critical role in securing wireless networks by ensuring that only authorized users can access network resources. The evolution from WPA2 to WPA3 represents significant advancements in security practices, addressing vulnerabilities and enhancing protection against unauthorized access. In enterprise environments, the use of RADIUS and 802.1x authentication further strengthens network security by providing robust mechanisms for user authentication and access control.
