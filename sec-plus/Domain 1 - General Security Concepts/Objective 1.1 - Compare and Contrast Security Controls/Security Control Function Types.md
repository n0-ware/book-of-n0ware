---
tags: 
topic: sec_general
subTopic: control_functional_types
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_sec_control_functional_types
cert: Sec+
---
# Security Control Function Types
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

**Security controls have both a category and a functional type related to the goal or function it performs.** These are preventative, detective, and corrective in most circumstances. Additionally, there can be directive, deterrent, and compensating. 

***Preventative --> Detective --> Corrective***

> At the time of intrusion attempt, preventive security control precedes an event and attempts to block it. Detective security control operates during an event to identify it and corrective security control mitigates following an event. Other control functional types are directive, deterrent, and compensating.
## Primary Functional Types
### Preventative
Designed to reduce or eliminate the likelihood attacks succeed and operate ***before*** attacks happen. 
- ACLs on firewalls and file systems
- AV or EDR blocking malicious file processes
- DNS white/blacklisting
### Detective
Identify and records attempted or successful attacks and operates ***during*** an attack. 
- Logs
- Physical inspection
### Corrective
Eliminates or reduces the impact of a security policy violation or an attack and is implemented ***after*** an attack. 
- Backup systems
- Patch management systems to close vulnerabilities
- Lessons learned sessions
## Secondary Functional Types
### Directive
Enforces a rule or behavior that is required such as those in a contract, policy, best practice, or SOP. 
- Contract language stating the impact of not following processes and procedures
- Training programs can also be considered directive (generally operational as well)
- Policies, procedures, guidelines
### Deterrent
Controls that do not physically (gate) or logically (ACL) prevent access but still serve to psychologically deter attackers or other malicious use or misuse.
- Warning signs
- Banners stating access is logged
### Compensating
These are *substitutes* for principal controls recommended by other standards and offer the same or better level of protection but applies that protection with a different methodology or technology.
- A single individual is responsible for the receipt and recording of financial transactions, but a manager is required to review them all at EoD. 