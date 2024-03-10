---
tags: 
topic: sec_threats_vulns_risk
subTopic: vulnerable_software
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_vulnerable_software
cert: Sec+
---
# Vulnerable Software Vectors
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Definition of Vulnerable Software
- **Nature**: Contains flaws in code or design exploitable to bypass access control or crash the process.
- **Exploitation Circumstances**: Typically specific and often swiftly patched by vendors.
- **Prevalence**: Almost all modern software has some vulnerabilities due to complexity and rapid release cycles.

## Ineffective Patch Management
- **Issue**: Organizations may lack an effective system to manage and apply patches.
- **Result**: Vulnerable software remains a common exploit vector.

## Impact of Operating Systems and Applications
- **Attack Surface Expansion**: More software increases potential attack surface.
- **Reduction Strategy**: Consolidating to fewer products and standardizing versions across the organization.

## Variability in Impact and Consequences
- **Examples**:
  - **Adobe PDF Reader Vulnerability**: Could give threat actors access to a corporate network.
  - **Server Software Vulnerability**: Might compromise cryptographic keys for secure web services.

## Unsupported Systems and Applications
- **Definition**: Systems no longer receiving updates and patches from vendors.
- **Risk**: High vulnerability to exploits if the organization cannot patch independently.
- **Management Strategy**: Isolating unsupported apps to reduce exploit opportunities, as a form of compensating control.

## Scanning Software for Vulnerability Management
- **Purpose**: Automates discovery and classification of software vulnerabilities.
- **Usage**: By organizations for security and by threat actors for reconnaissance.
- **Types**:
  - **Client-Based Agent**: Installed on each host, reports to a management server.
  - **Agentless Scanning**: Used for scanning without installation, often by threat actors.
