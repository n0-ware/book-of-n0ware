---
tags: 
topic: sec_monitoring
subTopic: networks_monitoring
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_networks_monitoring
cert: Sec+
---
# Monitoring Infrastructure
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Monitoring infrastructure is essential for maintaining the security and performance of network and computer resources. It involves various tools and protocols to collect and analyze data about network infrastructure and traffic flows.

## Network Monitors

- **Purpose**: To collect data on network infrastructure appliances like switches, routers, and firewalls.
- **Data Collected**: Includes load status for CPU/memory, disk capacity, fan speeds/temperature, network link utilization, and error statistics.
- **Heartbeat Messages**: Indicate the availability of network components.
- **SNMP (Simple Network Management Protocol)**:
  - Used for collecting network data.
  - SNMP traps alert the management system about notable events like port failure or excessive CPU utilization.
- **Alerts and Alarms**: Configurable thresholds for triggering alerts on hardware issues.

## NetFlow

- **Flow Collector**: Records metadata and statistics about network traffic, offering a comprehensive view of network activity without logging each packet.
- **Features**:
  - Trends and patterns identification for specific applications, hosts, and ports.
  - Anomaly detection and custom trigger alerts.
  - Visualization tools for easy interpretation of network connections and traffic patterns.
  - Identification of rogue user behavior, malware transmission, and bandwidth issues.
- **IP Flow Information Export (IPFIX)**: An IETF standard evolved from Cisco's NetFlow for reporting network flow information.
- **Flow Label and Record**:
  - Defined by packets sharing key characteristics (e.g., IP addresses, protocol type), known as a flow label.
  - A 5-tuple includes IP source/destination, protocol, source/destination ports, and protocol type. A 7-tuple adds the input interface and IP type of service.

## Tools for Monitoring

- **ntopng**: An example of a community edition tool used for monitoring NetFlow traffic data, showcasing network traffic patterns and providing insights into network health and security.

Monitoring infrastructure not only supports the day-to-day management of computer resources and network infrastructure but also plays a crucial role in detecting and responding to potential security threats. By employing tools and protocols like SNMP and NetFlow/IPFIX, organizations can enhance their visibility into network operations and improve their cybersecurity posture.
