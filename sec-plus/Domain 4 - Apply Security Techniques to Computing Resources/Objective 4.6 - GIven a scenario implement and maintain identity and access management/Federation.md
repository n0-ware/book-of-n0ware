---
tags: 
topic: sec_iam
subTopic: federation
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_authentication
cert: Sec+
---
# Federation
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Federation is the concept of making a network accessible to a broader audience beyond the organization's employees. It's crucial for scenarios like collaborating with partners, suppliers, and customers. Federation allows organizations to trust external networks for authentication and authorization.

## Use Cases

- In business, a company may need to provide access to its network for partners and customers.
- In the consumer world, users might want to use credentials from one platform to access another (e.g., Google and Twitter).

## Challenges and Solutions

- On-premises networks use LDAP, Kerberos, or Active Directory for centralized account management.
- Federation requires interoperability between different platforms and technologies.
- Claims-based identity is a common approach in federated authentication.

## Federation Process

![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_authentication_1.png]]

1. Principal wants to access a service provider (SP).
2. SP redirects the principal to an identity provider (IdP) for authentication.
3. Principal authenticates with IdP and receives a signed claim (token).
4. Principal presents the claim to SP.
5. SP validates the claim's signature based on trust with IdP.
6. SP determines permissions and attributes using its own database or IdP's user account profile (if authorized).

Federation enables secure cross-platform authentication and access.

