---
tags: 
topic: sec_network_arch
subTopic: sec_routing_infra
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_sec_routing_infra
cert: Sec+
---
# Routing Infrastructure Considerations
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Layer 3 Forwarding (Routing)
- **Function**: Applies logical addressing for network and subnet identification.
- **Architecture**: Represents logical segmentation and creation of subnetworks (subnets).
- **Broadcast Domains**: Each subnet is a separate broadcast domain.

## Internet Protocol (IP)
- **IPv4 Addressing**: 
  - Format: 32-bit address in dotted decimal notation.
  - Example: `10.1.1.0/24` indicates a network ID of `10.1.1.x` and a host ID.
  - Subnet Mask: `/24` equivalent to `255.255.255.0`.
- **IPv6 Addressing**: 
  - Format: 128-bit address using hex notation.
  - Example: `2001:db8::abc:0:def0:1234`.
  - Interface ID: Last 64-bits fixed for host's interface.
- **Address Resolution**: 
  - IPv4 uses ARP to map IP interface to MAC address.
  - IPv6 uses Neighbor Discovery (ND) protocol.

## Virtual LANs (VLANs)
- **Purpose**: Address mapping of logical IP topology to physical hardware switches.
- **Features**: 
  - Supports a range of VLAN IDs (2 to 4,094).
  - Allows segmenting ports on a switch into different VLANs.
- **Broadcast Domains**: Each VLAN operates as a separate broadcast domain.
- **Routing Requirement**: Traffic between VLANs must be routed.
- **Example**: Segmentation of workstation hosts (VLAN32) from VoIP handsets (VLAN40).

## VLAN Configuration in Network
- **Subnet Mapping**: Each VLAN maps to a separate IP subnet.
- **Communication Restriction**: Devices in different VLANs require a router to communicate.
- **Access Control**: Rules can prevent communication between VLANs if needed for security.
- **Expansion**: VLAN topology can extend across multiple switches for scalability.

## Hierarchical Design
- **Access Blocks**: Designated as separate IP subnets for easier access control.
- **Layer 3 Logical Addressing**: Facilitates writing access rules between network blocks or zones.

In summary, routing infrastructure in a network involves careful planning of IP addressing, subnetting, and VLAN configurations to ensure efficient traffic flow, security, and scalability.
