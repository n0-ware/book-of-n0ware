---
tags: 
topic: sec_threats_vulns_risk
subTopic: message_vectors
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_message_vectors
cert: Sec+
---
# Message Based Vectors
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Concept
- **Purpose**: Deliver file-based lures and trick users into executing them.
- **Attack Surface Consideration**: Features allowing direct messaging to network users.
## Delivery Mechanisms and Their Risks
- **Email**:
  - Method: Sending malicious file attachments or links via email.
  - Risk: Relies on social engineering to persuade users to open attachments.

- **Short Message Service (SMS)**:
  - Method: Sending files or links to mobile devices via text messaging.
  - Risks: Associated with vulnerabilities in SMS and SS7 protocol; lacks monitoring capabilities by organizations.

- **Instant Messaging (IM)**:
  - Platforms: Various services on Windows, Android, iOS, supporting file attachments.
  - Security: Generally more secure than SMS due to encryption, but may contain software vulnerabilities.

- **Web and Social Media**:
  - Method: Concealing malware in files attached to posts or available for download.
  - Risks: Potential for automatic infection via compromised sites (drive-by downloads); disinformation campaigns promoting malicious apps.
## Exploit Types
- **Zero-Click Exploits**: Triggered without user interaction, such as simply receiving an attachment or viewing a webpage.
## Persuasion and Pretexting
- **Objective**: Persuade users to reveal passwords or weaken security configurations.
- **Method**: Could involve direct communication like voice calls to users.
