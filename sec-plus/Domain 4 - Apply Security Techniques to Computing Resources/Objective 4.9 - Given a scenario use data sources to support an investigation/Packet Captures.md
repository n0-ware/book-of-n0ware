---
tags:
topic: "sec_information"
subTopic: "logs"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_logs" 
cert: "Sec+"
---
# Packet Captures
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Packet captures involve analyzing network traffic at the level of individual frames or using summary statistics of traffic flows and protocol usage. Packet captures provide valuable insights into network behavior and potential security breaches.

## SIEM and Packet Capture

- **SIEM Role**: SIEM (Security Information and Event Management) systems store selected information from sensors deployed at different network points.
- **Aggregation and Summarization**: Information captured from network packets is aggregated and summarized to depict overall protocol usage and endpoint activity.
- **Selective Recording**: Sensors are configured to record specific network packets that trigger firewall or IDS (Intrusion Detection System) rules.
- **Pivot to Packet Analysis**: SIEM software allows security teams to pivot from event or alert summaries to analyze the underlying packets in detail.

## Retrospective Network Analysis (RNA)

- **Full Network Event Recording**: RNA solutions, with sufficient resources, record the totality of network events at either a packet header or payload level.
- **Comprehensive Data**: RNA captures all network events, providing a comprehensive dataset for analysis.

## Packet Analysis

- **Deep Packet Inspection**: Packet analysis involves deep scrutiny of captured traffic using tools like Wireshark.
- **Decoding Packets**: Analyzers decode packets to display header fields at data link/MAC, network/IP, and transport (TCP/UDP) layers.
- **Application Layer Inspection**: It also examines application layer data, including header data and payload contents.
- **Use Cases**: Packet analysis identifies packet manipulation, data exfiltration attempts, suspicious domain or URL contacts, and reveals attack tools and potential malware.

Packet captures are crucial for in-depth network traffic analysis, allowing security teams to detect and investigate security incidents effectively.
