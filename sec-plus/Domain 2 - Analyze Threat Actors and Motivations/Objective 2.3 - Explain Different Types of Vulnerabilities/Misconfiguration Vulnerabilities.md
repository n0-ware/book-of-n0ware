---
tags: 
topic: sec_threats_vulns_risk
subTopic: misconfig_vulns
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_misconfig_vulns
cert: Sec+
---
# Misconfiguration Vulnerabilities
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
- **Cause**: Common source of security vulnerabilities due to incorrect setup of systems, networks, or applications.
- **Consequences**: Can lead to unauthorized access, data leaks, or full-system compromises.

## Common Areas of Misconfiguration
- **Network Equipment and Servers**: Default settings may compromise security.
- **Databases and Applications**: Overly permissive configurations expose sensitive information.
- **Cloud Environments**: Improperly managed access permissions on storage buckets can result in data leaks.

## Default Configurations Issues
- **Prioritization**: Ease of use and setup simplicity over security.
- **Risks**: Unnecessary services enabled, easily guessable default credentials, and overly permissive settings.
- **Examples**: Default "admin" credentials, vulnerable management protocols in network devices.

## Cloud Services Vulnerabilities
- **Defaults**: Often leave data storage or compute instances publicly accessible without proper configuration.

## Best Practices for Configuration
- **Principle of Least Privilege**: Essential for securing access and operations.
- **Configuration Steps**: Include changing default login credentials, tightening access controls, and regular audits.

## Support and Functional Issues
- **Temporary Changes**: Support actions may disable security features or loosen access controls, leading to vulnerabilities if not reverted.
- **Software Changes**: Installation or modification can introduce vulnerabilities.
- **Remote Support Tools**: Pose risks if not securely managed.

## Change Management Bypass
- **Urgent Issues and Outages**: Often addressed by bypassing best practices, leading to misconfigurations or system instability.
- **Documentation and Testing**: Changes made without proper documentation, testing, or approval.