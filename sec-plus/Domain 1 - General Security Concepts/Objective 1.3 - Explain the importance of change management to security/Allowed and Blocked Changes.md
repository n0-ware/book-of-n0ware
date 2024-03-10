---
tags:
topic: "sec_general"
subTopic: "allow_deny_lists"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_allow_deny_lists" 
cert: "Sec+"
---
# Allowed and Blocked Changes
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Allow Lists and Deny Lists
- **Role**: Crucial in change management for software and hardware control.
- **Perspectives**: Can be viewed in relation to change types or software restriction approaches.

## Allow Lists
- **Content**: Includes approved software, hardware, and specific low-risk change types.
- **Purpose**: Streamlines change management for trusted or preauthorized changes.
- **Authority Inclusion**: May list individuals with change management approval rights.
- **Maintenance**: Requires regular reviews for relevance to organizational needs.

## Deny (Block) Lists
- **Content**: Explicitly blocked software, hardware, and certain change types.
- **Purpose**: Prevents unauthorized or risky changes.
- **Examples**: Items with security/compatibility issues or high-risk changes.
- **Security Measure**: Clearly identifies prohibited changes, reducing misinterpretation.

## Technical Control Contexts
- **Application**: In access controls, firewall rules, and software restriction mechanisms.
- **Impact on Change Implementation**: Can cause unintended issues.
- **Example**: Patched software unrecognized in allow lists due to changed hash values, leading to usability problems.

## Incorporating Allow and Block Lists in Change Management
- **Importance**: Essential to consider in testing plans.
- **Software Restriction Policies**: May use file hash values for block lists.
## Restricted Activities
- **Definition**: Actions requiring extra scrutiny or higher approval due to potential impacts.
- **Contexts**: Critical systems, sensitive data, or regulatory compliance.
