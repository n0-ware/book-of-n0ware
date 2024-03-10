---
tags:
topic: "sec_network_arch"
subTopic: "net_device_placement"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_net_device_placement" 
cert: "Sec+"
---
# Device Placement
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Types of Controls and Placement Strategies

### Preventive Controls
- **Location**: Typically placed at the border of network segments or zones.
- **Function**: Enforce security policies on traffic entering and exiting the segment, ensuring confidentiality, integrity, and high availability.
- **Examples**: Firewalls for policy enforcement, Load balancers for high availability.

### Detective Controls
- **Location**: Positioned within the network perimeter to monitor internal traffic.
- **Function**: Alert on malicious traffic that has bypassed perimeter controls.
- **Examples**: Intrusion Detection Systems (IDS) monitoring internal traffic exchanges.

### Corrective Controls
- **Location**: Installed on hosts as part of endpoint protection.
- **Function**: Act on detections to mitigate threats, complementing network infrastructure controls.
- **Examples**: Endpoint protection software providing firewalls, antivirus, intrusion detection, and data loss prevention.

## Device Placement Illustration

![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_net_device_placement_1.png]]

- A router or Layer 3 switch connects to a border router or firewall, leading to three access switches:
  1. **First Access Switch**: Subnet `10.1.48.0/24`, connected to printers.
  2. **Second Access Switch**: Workstations and VoIP handsets, linked to VLAN 32 (`10.1.32.0/24`) and VLAN 40 (`10.1.40.0/24`).
  3. **Third Access Switch**: Private app and database servers, connected to VLAN 16 (`10.1.16.0/24`) and VLAN 24 (`10.1.24.0/24`).

- The border router/firewall interfaces with two additional switches:
  1. **First Switch**: Subnet `192.168.42.0/24`, connected to a Wi-Fi access point for the guest network.
  2. **Second Switch**: Subnet `172.16.0.0/24`, connected to public app servers.

### Security Control Placement
- **Preventive Control**: At the border router to regulate traffic.
- **Detective Control**: Between the router and firewall to monitor for malicious activity.
- **Corrective Control**: In untrusted zones to respond to detected threats.
- **Detective Controls**: At the third access switch to monitor sensitive internal traffic.
- **Multi-Type Controls**: At VLAN 32 and VLAN 16 for comprehensive security across different network layers.

## Conclusion
The careful placement of diverse security controls ensures a robust defense-in-depth strategy, protecting the network from external and internal threats. Each layer and segment of the network benefits from tailored security measures, enhancing overall security posture.
