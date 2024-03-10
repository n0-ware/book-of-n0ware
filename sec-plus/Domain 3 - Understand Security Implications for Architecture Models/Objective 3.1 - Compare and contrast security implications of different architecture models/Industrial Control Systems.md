---
tags:
topic: "sec_network_arch"
subTopic: "indsturial_systems"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_indsturial_systems" 
cert: "Sec+"
---
# Industrial Control Systems
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Workflow and Process Automation Systems
- **ICS**: Automate workflows and processes in critical infrastructure sectors including power, water, health services, telecommunications, and national security.
- **Distributed Control System (DCS)**: Manages process automation within a single site.
- **Components**:
  - **PLCs (Programmable Logic Controllers)**: Control machinery, linked via OT fieldbus or industrial Ethernet.
  - **Actuators and Sensors**: Operate mechanical components and monitor conditions.
  - **HMIs (Human-Machine Interfaces)**: Configure and output PLCs, can be local panels or software.
  - **Control Server**: Governs the entire process automation system.
  - **Data Historian**: Database for control loop information.

## Supervisory Control and Data Acquisition (SCADA)
- **Role**: Replaces control server in large-scale, multi-site ICSs, collecting data and managing embedded PLCs.
- **Communication**: Typically uses WAN communications like cellular or satellite.

## ICS/SCADA Applications
- **Energy**: Power generation and distribution.
- **Industrial**: Mining, refining raw materials with hazardous conditions.
- **Fabrication and Manufacturing**: Automated production systems requiring high precision.
- **Logistics**: Automated transport and tracking within factories or distribution to customers.
- **Facilities**: Automated HVAC, lighting, and security systems management.

## Security Concerns
- **Historical Context**: Initially built without IT security considerations, now recognizing the need for robust security controls.
- **Stuxnet Worm**: Example of a targeted attack on SCADA systems.
- **Priorities**: Safety, availability, and integrity are prioritized over confidentiality (AIC triad).

## Cybersecurity in ICS/SCADA
- **Importance**: Critical for public safety, economic stability, and national security.
- **Risks**: Include malware, ransomware, unauthorized access, and targeted attacks.
- **Protections**: Network segmentation, access controls, intrusion detection systems, encryption, and continuous monitoring.

ICS and SCADA systems are integral to the operation of critical infrastructure, requiring stringent cybersecurity measures to protect against potential attacks that could have severe consequences for society.
