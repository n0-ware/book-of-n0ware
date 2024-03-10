---
tags: 
topic: sec_applicaitons
subTopic: security
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_genera
cert: Sec+
---
# Application Protections
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Data Exposure Prevention

- **Cryptography**: Use industry-standard encryption libraries for secure data transmission.
- **Authentication**: Ensure data is only transmitted between authenticated hosts.

## Error Handling

- **Structured Exception Handler (SEH)**: Controls application behavior during exceptions.
- **Custom Error Handlers**: Preferable to default handlers to avoid revealing sensitive information.
- **Error vs. Exception**: Errors are irrecoverable, while exceptions can be handled without crashing.

## Memory Management

- **Avoid Insecure Practices**: Ensure proper checks when processing untrusted input to prevent overwriting memory.
- **Arbitrary Code Attacks**: Faulty memory management can allow attackers to execute their code.

## Client-Side vs. Server-Side Validation

- **Client-Side Validation**: Prone to malware interference, used for preliminary input checks.
- **Server-Side Validation**: Essential for security, performs final validation of input.
- **Best Practice**: Use both, with server-side as the critical security layer.

## Application Security in the Cloud

- **Cloud Hardening**: Includes least privilege access, encryption, and regular security assessments.
- **Shared Responsibility Model**: Cloud providers secure infrastructure, customers secure data and applications.

## Monitoring Capabilities

- **Enhanced Logging and Alerting**: Critical for detecting threats and supporting security audits.
- **Secure Coding Practices**: Encourage comprehensive logging and real-time alerting to improve incident response.
