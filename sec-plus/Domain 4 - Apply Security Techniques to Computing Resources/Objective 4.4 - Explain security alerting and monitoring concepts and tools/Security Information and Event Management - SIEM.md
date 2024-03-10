---
tags:
topic: "sec_monitoring"
subTopic: "siem"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_siem" 
cert: "Sec+"
---
# Security Information and Event Management - SIEM
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# Security Information and Event Management (SIEM)

SIEM software plays a crucial role in managing security data inputs from various sources, offering comprehensive reporting and alerting functionalities.

## Core Functions

- **Data Collection and Correlation**: Gathers data from network sensors, appliance/host/application logs, including switches, routers, firewalls, IDS sensors, packet sniffers, vulnerability scanners, malware scanners, and DLP systems.
- **Log Aggregation**: Normalizes data from different sources to make it consistent and searchable, using connectors or plug-ins for data interpretation.

## Data Collection Methods

### Agent-Based Collection

- **Description**: Involves installing an agent service on each host to filter, aggregate, and normalize logging data, which is then sent to the SIEM server.
- **Usage**: Common for Windows/Linux/macOS computers.
- **Resource Consumption**: Agents can use between 50–500 MB of RAM.

### Listener/Collector

- **Description**: Hosts push log changes to the SIEM server, which parses and normalizes the logs. This method does not require installing an agent on the host.
- **Usage**: Typically used for switches, routers, and firewalls.
- **Protocol**: Often utilizes Syslog protocol for log forwarding.

### Sensor

- **Description**: Collects packet captures and traffic flow data from network sniffers, either through mirror port functionality or network taps.
- **Usage**: For detailed network data collection.

## Log Aggregation

- **Purpose**: To make data from various sources consistent and searchable.
- **Process**:
  - **Parsing**: Interprets data from different system types and vendor implementations.
  - **Normalization**: Adjusts date/time zone differences to a unified timeline.
- **Implementation**: Requires specific parsers for each data source to map to standard fields in the SIEM's analysis tools.

SIEM tools are essential for cybersecurity
