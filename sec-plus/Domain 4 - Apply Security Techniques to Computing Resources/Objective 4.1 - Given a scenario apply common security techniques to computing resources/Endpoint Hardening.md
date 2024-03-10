---
tags:
topic: "sec_endpoints"
subTopic: "hardening"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_hardening" 
cert: "Sec+"
---
# Endpoint Hardening
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Operating System Security
- **Key Practices**: Access controls, authentication, secure configurations, application security, secure coding, patch management, endpoint protection, user awareness training, and monitoring.
- **Hardening**: The process of configuring an OS or application to enhance security.
- **Best Practice Baselines**: Industry standards for secure device configurations, emphasizing the principle of least functionality.

## Key Areas for Hardening
- **Interfaces**: Disable unused network interfaces to reduce attack surfaces.
- **Services**: Turn off unnecessary services to prevent exploitation.
- **Application Service Ports**: Disable or firewall off unused ports.
- **Persistent Storage**: Use disk encryption to secure data at rest.

## Workstations
- **Unique Concerns**: Workstations have a large attack surface due to varied tasks and applications.
- **Hardening Practices**: Remove unnecessary software, limit administrative privileges, manage applications strictly, and educate users on security threats.
- **Security Settings**: Implement automatic updates, screen locks, firewalls, endpoint protection, and device control policies.

## Baseline Configuration and Registry Settings
- **Purpose**: Ensure devices are configured according to security standards.
- **Windows Registry**: Central repository for Windows configuration settings.
- **Group Policy Objects (GPOs)**: Deliver policy settings to domain-joined computers.
- **Intrusion Detection**: Monitor for suspicious registry changes.

## Baseline Deviation Reporting
- **Tools**: Security Compliance Toolkit replaces older tools like MBSA for validating security configurations.
	- [Microsoft Security Compliance Toolkit Guide - Windows Security | Microsoft Learn](https://docs.microsoft.com/en-us/windows/security/threat-protection/security-compliance-toolkit-10)
- **Comparison**: Security Compliance Manager can compare production GPO settings against Microsoft's template policy settings.

Using comprehensive security practices and tools to harden endpoints is crucial for protecting against unauthorized access, data breaches, and malware infections. Establishing and adhering to security baselines ensures consistent and secure configurations across devices.
