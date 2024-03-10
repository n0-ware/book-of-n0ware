---
tags: 
topic: sec_threats_vulns_risk
subTopic: cred_replay_attacks
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_cred_replay_attacks
cert: Sec+
---
# Credential Replay Attacks
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# CREDENTIAL REPLAY ATTACKS

## Overview
Credential replay attacks are techniques used by threat actors to gain unauthorized access to network assets by exploiting cached credentials.

## Targeting Windows Active Directory Networks
- **Objective**: Compromise hosts on the network and escalate privileges.
- **Mechanism**: Exploits cached credentials in Windows environments.

## Cached Credentials in Windows
- **Local Security Authority Subsystem Service (LSASS)**: Caches various secrets for single sign-on.
- **Security Account Manager (SAM)**: Registry database storing credentials.
- **Cached Items**:
  - Kerberos Ticket Granting Ticket (TGT) and session key.
  - Service tickets for active application sessions.
  - NT hash of signed-in user and service accounts.
- **Credential Guard**: Windows feature protecting these secrets from malicious processes.

## Credential Replay Attack Methods
1. **Pass the Hash (PtH)**:
   - Obtains and uses NT hash to authenticate on other hosts.
   - Effective against services allowing NTLM authentication.
2. **Golden Ticket Attack**:
   - Forges a ticket granting ticket for unrestricted access to domain resources.
3. **Silver Ticket Attack**:
   - Forges service tickets (Pass the Ticket - PtT).

## Mitigations and Detection
- **Microsoft's Mitigations**: Patches and secure configurations to reduce attack effectiveness.
- **Detection**:
  - Security log event correlation (prone to false positives).
  - Antivirus and host-based intrusion detection systems.

Credential replay attacks pose a significant threat to network security, particularly in Windows-based environments. Understanding and mitigating these attacks require robust security measures, including system patching, secure configurations, and vigilant monitoring.


![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_cred_replay_attacks_2.png]]