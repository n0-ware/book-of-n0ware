---
tags: 
topic: sec_iam
subTopic: pam
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_access_control
cert: Sec+
---
# Privileged Access Management - PAM
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
- **Definition**: Policies, procedures, and technical controls that manage and secure privileged accounts.
- **Purpose**: Prevents the compromise of accounts with elevated privileges that can make significant system changes.

## Key Concepts
- **Standard Users**: Limited to running programs and modifying their own files.
- **Privileged Accounts**: Can configure hosts, manage network appliances, servers, and databases.

## PAM Controls
- **Identification and Documentation**: Provides visibility into privileged accounts and their usage.
- **Credential Management**: Ensures secure access to these accounts.

## Best Practices
- **Limit Administrative Accounts**: Reduces the risk of compromise.
- **Avoid Account Sharing**: Ensures accountability and traceability.
- **Use Strong Authentication**:
  - Strong passwords.
  - Multi-factor authentication (MFA) or passwordless authentication.
- **Secure Administrative Workstations (SAW)**: Minimizes the attack surface by limiting applications and services.

## Just-in-Time (JIT) Permissions and Zero Standing Privileges (ZSP)
- **Concept**: Elevated privileges are requested explicitly and granted temporarily, reducing the risk of unauthorized use.
  
### Models for JIT/ZSP Implementation
1. **Temporary Elevation**:
   - Grants administrative rights for a limited period.
   - Examples: UAC in Windows, sudo in Linux.
2. **Password Vaulting/Brokering**:
   - Privileges are "checked out" for limited use, requiring justification and possibly manual approval.
   - Offers enhanced accounting and security measures.
3. **Ephemeral Credentials**:
   - Creates temporary accounts or group memberships for specific tasks, which are then disabled or destroyed.

## Application to Service Accounts
- PAM practices also apply to service accounts, ensuring that automated processes also adhere to security protocols.

## Importance
- **Security Enhancement**: Mitigates risks associated with privileged account compromise.
- **Accountability**: Ensures actions can be traced to individual administrators.
- **Compliance**: Supports adherence to regulatory requirements and internal security policies.
