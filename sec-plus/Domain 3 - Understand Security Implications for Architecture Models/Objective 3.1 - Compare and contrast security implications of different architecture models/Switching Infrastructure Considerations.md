---
tags:
topic: "sec_network_arch"
subTopic: "switching_infra"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_switching_infra" 
cert: "Sec+"
---
# Switching Infrastructure Considerations
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Basic Function of Network Infrastructure
- **Purpose**: Forward traffic from one node to another.
- **Topology**: Diagram showing physical or logical connections between nodes.

## On-Premises Network (Enterprise LAN)
- **Type**: Network installed at a single site, operated by one company.
- **Focus**: Structured cabling in office and campus networks.

## Structured Cabling System
- **Components**:
  1. **Patch Cable**: Connects computer's network card to wall port.
  2. **Structured Cable**: Runs from wall port to patch panel through conduits.
  3. **Patch Panel**: Structured cable terminates here, another patch cable connects to switch port.
- **Topology**: Star topology with switch at the center and hosts radiating out.
- **Broadcast Domain**: Switch ensures broadcast messages reach all connected hosts.

## Topology Drawbacks and Hierarchical Design
- **Issues with Star Topology**:
  - Large broadcast domains may suffer performance issues.
  - Flat network segment poses security challenges.
- **Hierarchical Design**:
  - Access blocks served by access switches.
  - Routers connect access switches, creating separate broadcast domains.
  - Zone-based security model implementation.

## Network Hierarchy and Layer 3 Switches
- **Layer 3 Switches**: Perform both routing and switching, crucial for core network.
- **Roles**: Different switch types for various roles in network architecture.

## Server and Core Network Connectivity
- **Location**: Servers and core appliances in a secure equipment or server room.
- **Connection**: Servers directly connected to switch ports using patch cables.

Understanding the structured cabling system and hierarchical network design is key to optimizing performance and security in on-premises networks.
