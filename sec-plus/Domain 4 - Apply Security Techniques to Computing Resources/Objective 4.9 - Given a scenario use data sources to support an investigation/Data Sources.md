---
tags:
topic: "sec_information"
subTopic: "data_sources"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_data_sources" 
cert: "Sec+"
---
# Data Sources
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

In the realm of incident response and digital forensics investigations, data sources play a crucial role in discovering indicators. These investigations rely on diverse data sources, including:

- System memory and media device file system data and metadata.
- Log files from network appliances (switches, routers, firewalls/UTMs).
- Captured network traffic.
- Alerts from intrusion detection systems.
- Log files from network-based vulnerability scanners.
- Log files from client and server host computers.
- Log files from applications and services on hosts.
- Alerts from endpoint security software (e.g., host-based intrusion detection, antivirus).

Managing the vast and varied data sources can be challenging, and organizations use Security Information and Event Management (SIEM) tools to aggregate and correlate these sources. SIEM tools provide event dashboards and automated reports, making incident response more efficient. However, dealing with large amounts of data involves addressing the "Vs" of data challenges: volume, velocity, variety, veracity, and value.

### Dashboards

- Event dashboards offer a centralized view for incident response tasks.
- Dashboards cater to different purposes, with customized views.
- An incident handler's dashboard displays uncategorized events assigned to them and key status metrics.
- A manager's dashboard shows overall status indicators for all event handlers.

### Automated Reports

- SIEM tools enable two types of reporting: alerts and status reports.
- Alerts trigger incident cases and form a significant part of an analyst's workload.
- Status reports provide data about threat levels, incident counts, security control effectiveness, and are crucial for management decisions and compliance reporting.
- SIEMs offer preconfigured dashboards and reports, with the option to create custom reports.
- Tailoring reports to the intended audience's needs and goals is essential for effective incident response.

This summary emphasizes the importance of data sources, dashboards, and reports in incident response and highlights the need for customization to ensure actionable insights.