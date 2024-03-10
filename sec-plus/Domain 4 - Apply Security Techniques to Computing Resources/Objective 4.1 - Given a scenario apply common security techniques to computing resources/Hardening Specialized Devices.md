---
tags:
topic: "sec_endpoints"
subTopic: "hardening"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_hardening" 
cert: "Sec+"
---
# Hardening Specialized Devices
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Overview
Industrial Control Systems (ICS), Supervisory Control and Data Acquisition (SCADA) systems, embedded systems, Real-Time Operating Systems (RTOS), and Internet of Things (IoT) devices are increasingly targeted due to their critical roles in infrastructure. While general hardening strategies like regular updates and disabling unnecessary services apply, these systems require specialized approaches due to their unique operational environments and constraints.

## Hardening ICS/SCADA
- **Network Segmentation**: Isolate ICS/SCADA from broader networks to limit exposure to threats.
- **Authentication and Authorization**: Implement robust processes to strictly control system access.
- **Physical and Cyber Threat Protection**: Breaches can lead to significant physical and environmental harm, necessitating dual-focus security measures.
- **Unidirectional Gateways**: Use data diodes to ensure data only flows outward, protecting against inbound attacks.

## Hardening Embedded and RTOS
- **Security by Design**: Incorporate security measures from the initial design phase, focusing on secure coding practices and minimal design to limit attack surfaces.
- **Secure Boot Mechanisms**: Ensure that devices only boot with verified and trusted software to prevent tampering.
- **Physical Security**: Implement tamper-proofing measures to protect device integrity.
- **Device Selection**: Choose devices based on their security capabilities, not just functionality and cost.

## IoT Device Hardening
- **Tailored Security Approaches**: Given the diverse nature of IoT devices, hardening requires specific strategies that address both cyber and privacy concerns.
- **Minimal Functionality**: Like RTOS, IoT devices should be designed to perform only necessary functions to minimize vulnerabilities.

## Security Standards and Certifications
- **Common Criteria (ISO/IEC 15408)**, **IEC 62443**, **MISRA-C**, and **CERT Secure Coding Standards** provide guidelines and best practices for designing and evaluating the security of RTOS and embedded systems.
- **Certifications such as ISO 27001 and IEC 61508** demonstrate compliance with security standards, offering assurances about a system's security posture.

### Importance
Security standards and certifications are crucial for establishing a robust framework for assessing and validating security controls in specialized devices. They offer a common language for evaluating security, enhancing confidence in device security capabilities.

For more detailed information on Common Criteria, visit [Common Criteria Portal](https://www.commoncriteriaportal.org).

## Conclusion
Specialized devices play a pivotal role in today's infrastructure and thus require dedicated hardening strategies that go beyond conventional cybersecurity measures. Tailoring approaches to the unique needs of ICS/SCADA, RTOS, embedded systems, and IoT devices, while adhering to relevant security standards and certifications, is essential for safeguarding critical infrastructure.
