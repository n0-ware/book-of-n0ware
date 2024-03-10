---
tags:
topic: "sec_information"
subTopic: "metadata"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_metadata" 
cert: "Sec+"
---
# Metadata
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Metadata refers to the properties of data, including attributes related to its creation, storage, or transmission. Investigating incidents often involves examining metadata sources to establish timelines and gather evidence.

## File Metadata

- **Attributes**: File systems track attributes such as creation, access, and modification timestamps.
- **Security Attributes**: Files can have security attributes like read-only, hidden, or system file flags.
- **Permissions**: ACLs (Access Control Lists) define file permissions.
- **Extended Attributes**: Files may have extended attributes, including author information, copyright details, and indexing tags.

## Web Metadata

- **HTTP Headers**: When a client requests a resource from a web server, headers are exchanged to set properties and transmit authorization information.
- **Cookies**: Headers can include cookies for authentication.
- **Data Type**: Headers describe the type of data returned (e.g., text or binary).
- **Logging**: Web servers may log header information.

## Email Metadata

- **Internet Header**: Email headers contain sender and recipient addresses, server details, and transmission history.
- **Header Flow**: Email headers evolve as the message travels through mail agents (MUA, MDA, MTA).
- **Parsing Tools**: Tools like Message Analyzer help parse and display email headers more clearly.
- **Information Sources**: MTAs add information, including spam checking results, to email headers.

Metadata is a valuable source of information in investigations, helping determine when and where incidents occurred and providing evidence for analysis.
