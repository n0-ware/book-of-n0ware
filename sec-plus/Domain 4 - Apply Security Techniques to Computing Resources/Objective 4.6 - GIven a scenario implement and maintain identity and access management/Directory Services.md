---
tags:
topic: "sec_iam"
subTopic: "identity"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_identity" 
cert: "Sec+"
---
# Directory Services
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Overview
- Directory services store information about users, computers, security groups/roles, and services.
- Each directory object has various attributes.
- Directory schema defines attribute types, their data, and whether they are mandatory or optional.
- Interoperability is often achieved using the Lightweight Directory Access Protocol (LDAP), derived from X.500.

## Distinguished Name (DN)
- A DN uniquely identifies a resource in an X.500-like directory.
- Composed of attribute-value pairs separated by commas.
- Attributes listed from most specific to progressively broader.
- The most specific attribute is the relative distinguished name (RDN), identifying the object within parent attribute values.

## Common Attributes
- Common attributes used in DNs include:
  - Common Name (CN)
  - Organizational Unit (OU)
  - Organization (O)
  - Country (C)
  - Domain Component (DC)

## Example DN
- Example DN for a web server operated by Widget in the UK:
  - `CN=WIDGETWEB, OU=Marketing, O=Widget, C=UK, DC=widget, DC=foo`
