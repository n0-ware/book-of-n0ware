---
tags:
topic: ""
subTopic: "malicious_code_iocs"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_malicious_code_iocs" 
cert: "Sec+"
---
# Malicious Code Indicators
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Overview
Indicators of malicious code execution can be detected by endpoint protection software or identified post-attack in system logs, revealing interactions with the network, file system, and registry.

## Types of Malicious Activity
1. **Shellcode**:
   - **Function**: Exploits OS or app vulnerabilities to gain privileges or install backdoors.
   - **Behavior**: Establishes network connections to download additional tools.

2. **Credential Dumping**:
   - **Targets**:
     - Credentials file (SAM) on a local Windows workstation.
     - Credentials in memory handled by `lsass.exe`.
   - **DCSync Attack**: Tricks a domain controller to replicate credentials to a rogue host.

3. **Pivoting/Lateral Movement/Insider Attack**:
   - **Method**: Uses remote execution tools (e.g., PsExec, PowerShell) for network exploration or configuration changes.
   - **Objective**: Access data assets, widen network access, or alter system security settings.

4. **Persistence**:
   - **Mechanisms**: Utilizes AutoRun registry keys, scheduled tasks, or WMI event subscriptions.
   - **Purpose**: Ensures the backdoor remains active after reboots or user log-offs.

Understanding these indicators and the behavior of malicious code is crucial for effective detection, response, and mitigation of network security threats.
