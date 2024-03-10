---
tags:
topic: ""
subTopic: "network_attacks"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_network_attacks" 
cert: "Sec+"
---
# Network Attacks
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
Network attacks encompass a range of strategies and techniques used to disrupt or gain unauthorized access to systems via network vectors.

## Cyberattack Lifecycle Stages
1. **Reconnaissance**:
   - **Scanning Tools**: Used for host discovery, service discovery, and fingerprinting.
   - **IP Addresses and Port Identification**: Determines active IP addresses and open TCP/UDP ports.
   - **Fingerprinting**: Identifies software types, versions, and operating system details.
   - **Challenges**: Differentiating between malicious and non-malicious scanning activity.

2. **Credential Harvesting**:
   - **Objective**: Acquire passwords or cryptographic secrets for authenticated network access.

3. **Denial of Service (DoS)**:
   - **Impact**: Makes hosts and services unavailable.
   - **Detection**: Monitoring tools reporting unresponsiveness or high request volumes.

4. **Weaponization, Delivery, and Breach**:
   - **Methods**: Directing malicious code at vulnerable hosts/services or tricking users into running malware.

5. **Command and Control (C2/C&C), Beaconing, and Persistence**:
   - **Operation**: Remote operation and maintenance of access to compromised hosts.
   - **Detection**: Identifying anomalous connection endpoints and compromised host indicators.

6. **Lateral Movement, Pivoting, and Privilege Escalation**:
   - **Process**: Moving across the network and obtaining higher permissions.
   - **Detection**: Monitoring anomalous account logins and privilege use, often requiring machine learning-backed software.

7. **Data Exfiltration**:
   - **Action**: Transferring information assets to the attacker's machine.
   - **Indicators**: Anomalous large data transfers or stealthy small data movements.

## Iterative Nature of Attacks
- **Initial Foothold**: Achieved through external reconnaissance and credential harvesting or breach.
- **Internal Expansion**: Conducting further reconnaissance and credential harvesting for lateral movement and privilege escalation on internal hosts.

Understanding these stages and techniques is vital for effectively detecting, responding to, and mitigating network attacks, as well as for developing robust network security strategies.
