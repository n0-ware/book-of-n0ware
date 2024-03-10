---
tags:
topic: "sec_information"
subTopic: "logs"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_logs" 
cert: "Sec+"
---
# Application and Endpoint Logs
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Application logs and endpoint logs are essential sources of information for monitoring and securing hosts. They provide insights into application-specific events and the activities of security software running on the host.

## Application Logs

- **Definition**: Application logs are managed by applications rather than the operating system (OS). They can use standard formats like Event Viewer or syslog, or proprietary formats chosen by developers.
- **Windows Event Viewer**: In Windows, there's a dedicated application log that any authenticated account can write to. Custom application and service logs are managed by specific processes, and the choice of log depends on the app's developer.
- **Location**: Check the product documentation to determine where events for a specific software application are logged.

## Endpoint Logs

- **Definition**: Endpoint logs refer to events monitored by security software running on the host. This includes host-based firewalls, intrusion detection systems, vulnerability scanners, and antivirus/antimalware protection suites.
- **Endpoint Protection Platforms (EPPs)**: Suites that integrate these functions are often referred to as endpoint protection platforms (EPPs), enhanced detection and response (EDR), or extended detection and response (XDR).
- **Integration with SIEM**: Security tools for endpoints can be integrated with a SIEM using agent-based software.
- **Monitoring Threat Levels**: Summarizing events from endpoint protection logs can provide insights into overall threat levels, such as malware detection, host intrusion detection events, and missing patches on hosts.
- **Attribution and Threat Intelligence**: Close analysis of detection events helps attribute intrusion events to specific actors and develop threat intelligence regarding tactics, techniques, and procedures.

## Vulnerability Scans

- **Definition**: Vulnerability scans are conducted to identify security weaknesses, including missing patches and noncompliance with security configurations.
- **Logging Vulnerabilities**: A vulnerability scanner can be configured to log each detected vulnerability to a SIEM, allowing for a detailed analysis of host vulnerabilities.
- **Configuration Insights**: The logs provide information about whether a host is properly configured, helping organizations maintain security compliance.

Application and endpoint logs are valuable sources of information for both monitoring and enhancing the security posture of hosts within an organization.
