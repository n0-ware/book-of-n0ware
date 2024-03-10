---
tags:
topic: "sec_data"
subTopic: "dlp"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_dlp" 
cert: "Sec+"
---
# Data Loss Prevention
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Data Loss Prevention (DLP) is essential for organizations that handle large volumes of sensitive data, including personal information and intellectual property (IP). DLP solutions offer automated tools to assist with data classification, applying guardianship policies, and ensuring data is not improperly accessed or transferred. Here's a concise overview of DLP components and functionalities:

### DLP Components:

- **Policy Server:** Centralized configuration of data classification, confidentiality, privacy rules, incident logging, and reporting.
- **Endpoint Agents:** Enforce policies on client computers, ensuring protection even when devices are offline or outside the network.
- **Network Agents:** Scan communications at network perimeters, interfacing with web and messaging servers to enforce policies.

### DLP Functionality:

- **Content Scanning:** DLP solutions scan both structured (e.g., databases) and unstructured data (e.g., emails, documents) for sensitive content.
- **File Cracking:** Unstructured data is processed into a scannable format, allowing the DLP system to monitor and block unauthorized data transfers.
- **Removable Media and Online Communications:** DLP can restrict data transfer to USB devices, emails, instant messaging, social media, and cloud storage services.

### Remediation Mechanisms:

- **Alert Only:** Policy violations are logged, and administrators may be alerted, but the copying action is allowed.
- **Block:** Prevents file copying, logs the incident, and may alert the user to the violation.
- **Quarantine:** Restricts access to the violated file, potentially encrypting it or moving it to a quarantine area.
- **Tombstone:** Replaces the original file with a placeholder explaining the violation and potential release methods.

DLP ensures that sensitive data is not lost, misused, or accessed by unauthorized individuals, providing comprehensive protection for an organization's critical information assets