---
tags:
topic: "sec_endpoints"
subTopic: "protection"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_protection" 
cert: "Sec+"
---
# Endpoint Protection
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Segmentation
- **Purpose**: Reduces the impact of cybersecurity incidents by isolating systems.
- **Implementation**: Divides networks into separate segments with distinct security controls.
- **Benefits**: Limits attack spread, enhances data protection, and provides granular control over access.

## Isolation
- **Definition**: Segregates individual devices to limit their interaction and reduce attack surfaces.
- **Objective**: Prevents lateral movement of threats across devices.
- **Approach**: Restricts network traffic between devices to minimize potential vulnerabilities.

## Antivirus and Antimalware
- **Evolution**: From signature-based detection to comprehensive malware protection.
- **Limitation**: Signature-based detection alone is insufficient against modern threats.
- **Role**: Remains a crucial layer in defending against various forms of malware.

## Disk Encryption
- **Full Disk Encryption (FDE)**: Encrypts the entire contents of a drive to protect data at rest.
- **Key Storage**: Typically secured in a Trusted Platform Module (TPM) or on a removable USB drive.
- **Self-Encrypting Drives (SED)**: Perform cryptographic operations at the drive controller level for performance efficiency.

## Patch Management
- **Challenge**: Timely application of patches to address vulnerabilities.
- **Automated Scanners**: Identify missing patches for operating systems, third-party apps, and devices.
- **Enterprise Patch Management**: Suites help manage and deploy patches across diverse systems.
- **Testing**: Essential before deploying patches to avoid introducing new vulnerabilities or disrupting operations.

### Key Considerations
- **Enterprise Networks**: Caution with auto-updates to avoid compatibility issues.
- **Legacy Systems**: May require compensating controls if patches are not available.
- **Testing and Deployment**: Critical for ensuring patch reliability and system stability.

Segmentation, isolation, and comprehensive malware defense mechanisms are fundamental to enhancing endpoint security. Disk encryption safeguards data against unauthorized access, while effective patch management ensures vulnerabilities are promptly addressed. Together, these strategies form a robust framework for securing endpoints against a wide range of security threats.
