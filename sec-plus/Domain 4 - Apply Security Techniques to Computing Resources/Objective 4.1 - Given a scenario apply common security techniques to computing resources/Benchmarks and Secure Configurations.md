---
tags: 
topic: sec_computing
subTopic: benchmarks
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_benchmarks
cert: Sec+
---
# Benchmarks and Secure Configurations
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Secure baselines and benchmarks play a pivotal role in ensuring IT security, manageability, and operational efficiency by standardizing configurations across network devices, software, and systems.

## Key Resources for Secure Configuration
- **Center for Internet Security (CIS) Benchmarks**: Offer globally recognized best practices for securing IT systems, covering networks, operating systems, applications, and compliance with frameworks like PCI DSS, NIST 800-53, SOX, and ISO 27000.
- **Security Technical Implementation Guides (STIGs)**: Developed by the Defense Information Systems Agency (DISA) for the US Department of Defense, providing security configurations designed for DoD IT infrastructure.

## Tools and Technologies for Compliance Management
- **Configuration Management Tools**: [Puppet](https://www.puppet.com/), [Chef](https://www.chef.io/), [Ansible](https://www.ansible.com/), and Microsoft's Group Policy automate the deployment of secure configurations.
- **Compliance Monitoring Tools**: SCAP compliant tools, like [OpenSCAP](https://www.open-scap.org/) and [CIS-CAT Pro](https://www.cisecurity.org/cybersecurity-tools/cis-cat-pro), assess system adherence to secure baselines.
- **SCAP Compliance Checker (SCC)**: Maintained by DISA for measuring compliance with [STIG](https://public.cyber.mil/stigs/scap/) baselines.

## Hardening Concepts
Improving the security of devices and systems by altering default configurations to prevent cyberattacks.

### Switches and Routers Hardening
- Change default credentials.
- Disable unnecessary services and interfaces.
- Use secure management protocols (SSH, HTTPS).
- Implement Access Control Lists (ACLs).
- Enable logging and monitoring.
- Configure port security.
- Enforce strong password policies.
- Ensure physical security of equipment.

### Server Hardware and Operating Systems Hardening
- Change default credentials.
- Disable unnecessary services.
- Apply security patches and updates regularly.
- Implement the least privilege principle.
- Use firewalls and intrusion detection systems.
- Secure configuration following CIS benchmarks or STIGs.
- Implement strong access controls, including MFA and PAM.
- Enable logging and monitoring.
- Deploy antivirus and antimalware solutions.
- Ensure physical security of server equipment.

## Summary
Adhering to secure baselines and benchmarks is essential for protecting IT infrastructure from vulnerabilities and cyber threats. Utilizing configuration management and compliance monitoring tools facilitates the enforcement of these standards, while hardening practices further secure network devices and systems against unauthorized access and attacks.
