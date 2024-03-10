---
tags:
topic: "sec_network_arch"
subTopic: "sdn"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_sdn" 
cert: "Sec+"
---
# Software Defined Networking
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Overview
SDN is a transformative approach to network management that enables dynamic, programmatically efficient network configuration to improve network performance and monitoring. It separates the network's control logic from the underlying routers and switches, promoting programmability and agility.

## Key Components of SDN
- **Control Plane**: Responsible for making decisions on how traffic is prioritized, secured, and routed through the network.
- **Data Plane**: Handles the actual switching and routing of traffic based on the control plane's decisions, and imposes security access controls.
- **Management Plane**: Monitors traffic flow and network status, providing an overview of the network's health and performance.

## Interaction Between Components
- **SDN Applications**: Define policy decisions on the control plane.
- **Network Controller Application**: Implements decisions on the data plane, interfacing with network devices via APIs.
- **Northbound API**: Interface between SDN applications and the SDN controller.
- **Southbound API**: Interface between the controller and network devices (physical and virtual appliances).

## Network Functions Virtualization (NFV)
- **Concept**: Complements SDN by supporting the rapid deployment of virtual networking functions on general-purpose VMs and containers.
- **Goal**: To virtualize network services traditionally run on proprietary, dedicated hardware.

## Benefits of SDN
- **Simplified Management**: Abstracts away the complexity of individual device configurations, aligning network policies with business objectives.
- **Automated Deployment**: Facilitates the automatic provisioning of network links, appliances, and servers, enhancing operational efficiency.
- **Flexibility**: Enables rapid adaptation to changing network requirements and conditions.

SDN represents a pivotal shift towards more agile and programmable network infrastructures, supporting the evolving demands of modern computing environments and cloud architectures.


