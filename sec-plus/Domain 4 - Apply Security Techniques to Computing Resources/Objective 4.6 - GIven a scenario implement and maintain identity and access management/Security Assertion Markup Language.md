---
tags:
topic: "sec_iam"
subTopic: "federation"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_federation" 
cert: "Sec+"
---
# Security Assertion Markup Language (SAML)
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

In a federated network or cloud environment, specific protocols and technologies are needed to manage user identity assertions and transmit claims between different entities. One such solution is the **Security Assertion Markup Language (SAML)**.

## Key Characteristics

- SAML assertions (claims) are written in XML (eXtensible Markup Language).
- Communication is established using HTTP/HTTPS and the Simple Object Access Protocol (SOAP).
- Secure tokens are signed using the XML signature specification, ensuring the trustworthiness of the identity provider.

## Use Case Example: Amazon Web Services (AWS)

- AWS serves as a SAML service provider, enabling companies to manage user identities and permissions for cloud applications without creating separate accounts on AWS. This is achieved through SAML-based authentication.

## SAML Assertion Example (Simplified)

```xml
<samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion" ID="200" Version="2.0"
IssueInstant="2020-01-01T20:00:10Z" Destination="https://sp.foo/saml/acs" InResponseTo="100">

  <saml:Issuer>https://idp.foo/sso</saml:Issuer>
  <ds:Signature>...</ds:Signature>
  <samlp:Status>...(success)...</samlp:Status>
  
  <saml:Assertion xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:xs="http://www.w3.org/2001/XMLSchema" ID="2000" Version="2.0"
    IssueInstant="2020-01-01T20:00:09Z">
  
    <saml:Issuer>https://idp.foo/sso</saml:Issuer>
    <ds:Signature>...</ds:Signature>
    <saml:Subject>...</saml:Subject>
    <saml:Conditions>...</saml:Conditions>
    <saml:AudienceRestriction>...</saml:AudienceRestriction>
    <saml:AuthnStatement>...</saml:AuthnStatement>
    
    <!-- AttributeStatement, Attributes, and more... -->
    
  </saml:Assertion>
</samlp:Response>
