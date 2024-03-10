---
tags:
topic: "sec_iam"
subTopic: "sso"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_sso" 
cert: "Sec+"
---
# Single Sign-On Authorization
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Authentication Process

1. User enters the correct password.
2. Client decrypts the Ticket Granting Service (TGS) session key, ensuring the shared secret is known.
3. Client cannot interfere with the Ticket Granting Ticket (TGT).
4. To access resources, the principal requests a service ticket from TGS.

## Requesting a Service Ticket

1. Principal sends TGS its TGT, target application server name, and an authenticator.
2. TGS decrypts messages using KDC's secret key (first) and TGS session key (second) to verify authenticity.
3. TGS checks ticket expiration and prevents replay attacks.
4. TGS responds with a service session key and an encrypted service ticket.

## Accessing the Application Server

1. Principal forwards the service ticket to the application server along with another time-stamped authenticator.
2. Application server decrypts the service ticket and authenticator using its secret key.
3. Optionally, the server responds with a time stamp encrypted using the service session key.
4. Mutual authentication is achieved, ensuring the server is trustworthy.

## Server Response

1. The server now responds to access requests according to its access control list.
2. Kerberos prevents on-path attacks and provides mutual authentication.

## Drawbacks

- Kerberos has a single point of failure in the Key Distribution Center (KDC).
- Backup KDC servers can be implemented for redundancy (e.g., Active Directory supports multiple domain controllers).

