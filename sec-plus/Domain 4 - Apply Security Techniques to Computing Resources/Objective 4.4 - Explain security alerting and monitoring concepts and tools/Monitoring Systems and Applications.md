---
tags:
topic: "sec_monitoring"
subTopic: "systems_and_apps"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_systems_and_apps" 
cert: "Sec+"
---
# Monitoring Systems and Applications
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Monitoring systems and applications are critical for maintaining operational security and performance. Dashboards and reports offer real-time insights into system and application health, while logs provide valuable data for security analysis.

## System Monitors and Logs

- **System Monitors**: Similar to network monitors, but for computer hosts, reporting health status using SNMP traps.
- **Logs**:
  - Essential for diagnosing issues and recording both authorized and unauthorized resource usage.
  - Serve as an audit trail and an early warning system for intrusion attempts.
  - Critical for tying actions to specific users, highlighting the importance of unique login credentials.

## Application and Cloud Monitors

- **SNMP Limitations**: Proprietary solutions often offer more comprehensive monitoring for various environments (on-premises, cloud, hybrid).
- **Monitoring Features**: Include heartbeat tests, session and request numbers, bandwidth, CPU/memory utilization, and alert conditions.
- **Cloud Monitoring**: Focuses on bandwidth, VM status, and application health.

## Vulnerability Scanners

- **Function**: Reports unmitigated vulnerabilities for each host, aiding in network-wide security assessments.
- **Use**: Helps identify patching or configuration issues across the network.

## Antivirus (Endpoint Protection Platforms)

- **Scope**: Beyond traditional antivirus functions, modern suites offer comprehensive endpoint protection, including UEBA and AI-backed threat detection.
- **Integration**: Can be configured to generate dashboard alerts or logs for SIEM systems.

## Data Loss Prevention (DLP)

- **Purpose**: Controls the copying of sensitive data to ensure it only moves to authorized destinations.
- **Monitoring**: Tracking DLP policy violations can indicate security issues, especially when analyzed for trends over time.

Effective monitoring of systems and applications is a foundational aspect of cybersecurity, enabling organizations to detect, analyze, and respond to security threats proactively.
