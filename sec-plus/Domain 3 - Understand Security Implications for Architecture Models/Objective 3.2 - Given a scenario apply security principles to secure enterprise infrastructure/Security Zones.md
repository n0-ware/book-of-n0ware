---
tags:
topic: "sec_network_arch"
subTopic: "net_sec_zones"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_net_sec_zones" 
cert: "Sec+"
---
# Security Zones
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# SECURITY ZONES IN NETWORK ARCHITECTURE

Security zones are critical in defining and implementing a zone-based security topology within network architecture. These zones help manage trust levels, access controls, and protect sensitive data by segregating network segments based on their security requirements.

## Key Principles of Security Zones
- **Organizational Boundary**: Differentiates between trusted internal hosts and untrusted external hosts in the public Internet zone.
- **Analysis of Systems and Data Assets**: Identifies systems and data with similar access control requirements to map out the internal security topology.
- **Confidentiality and Integrity**: Prioritizes for database and file systems hosting sensitive company and personal data.
- **Integrity and Availability**: Focuses on client devices and public-facing application servers, which should not store sensitive data.
- **Comprehensive Protection**: Application servers supporting network infrastructure require high levels of confidentiality, integrity, and availability due to their potential impact on the network if compromised.

## Segregation and Traffic Control
- **Physical/Logical Segmentation**: Ensures security zones are segregated to prevent unauthorized access and data breaches.
- **Traffic Control via Firewalls**: Manages traffic between zones based on the principle of least privilege, allowing only necessary communications.
- **Known Entry and Exit Points**: Mandates that each zone must have a defined access point to maintain security integrity.

## Hierarchy and Access Rules
- **Low Privilege Zones**: Contain less secure hosts, like printers, which can accept connections but not initiate them.
- **Enterprise LAN**: Allows client devices to make authorized requests across zones but restricts incoming connections.
- **Guest Zone**: Provides Internet access without permitting entry to the enterprise LAN.
- **Public-facing Servers**: Can receive requests from the Internet but are restricted from initiating requests to both the enterprise LAN and the Internet.

## VLANs and Additional Rules
- **Intra-zone Communication**: Within the same zone, VLANs can enforce additional access rules, such as allowing application servers to request data from databases but preventing the reverse.

The implementation of security zones within a network architecture plays a vital role in ensuring the security and integrity of data and systems by carefully controlling access and interactions between different network segments.

## Network Configuration

![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_net_sec_zones_1.png]]
- **Inline Proxy Firewall**: Connected to a border router/firewall, subnet `10.1.128.0/24`.
- **Access Switches**: Three switches connecting various network segments.
  - **First Access Switch**: Subnet `10.1.48.0/24`, connected to printers.
  - **Second Access Switch**: Connected to workstations and VoIP handsets, linked to VLANs 32 (`10.1.32.0/24`) and 40 (`10.1.40.0/24`).
  - **Third Access Switch**: Connected to private app and database servers, linked to VLANs 16 (`10.1.16.0/24`) and 24 (`10.1.24.0/24`).
- **Border Router/Firewall**: 
  - Connected to two access switches for guest network (`192.168.42.0/24`) and public app servers (`172.16.0.0/24`).

## Security Zones
- **Zone 1, Low Privilege**: Printers (`10.1.48.0/24`).
- **Zone 2, Medium Privilege**: Workstations and VoIP handsets.
- **Zone 3, Untrusted**: Guest network and public app servers.
- **Zone 4, Internet**: External network connectivity.
- **Zone 5, High Privilege**: Private app and database servers.

## Traffic Control Between Zones
- **Medium to Low Privilege**: Default accept new connections from medium to low.
- **Low to Medium Privilege**: Block all new connections.
- **Subnet Restrictions**:
  - `10.1.32.0/24` blocks new connections from `10.1.40.0/24` and vice versa.
  - `10.1.16.0/24` blocks new connections from `10.1.24.0/24`.
  - `10.1.24.0/24` accepts most new connections from `10.1.16.0/24`.
- **Internet to Medium Privilege**: Default block, with some exceptions for new connections.
- **Medium to High Privilege**: Prevents new connections from high to medium; high accepts some new connections from medium.
- **Border Router to Untrusted Zone**: Prevents new connections from untrusted zones.
- **Untrusted to Border Router**: Blocks new connections.
- **Border Router Ports**:
  - Associated with `192.168.42.0/24` blocks new connections from the internet; internet accepts most new connections.
  - Associated with `172.16.0.0/24` accepts most new connections from the internet; internet blocks new connections from this port.

This configuration outlines a structured approach to network security, segregating devices and services into distinct zones with tailored access controls to mitigate risks and protect sensitive data.
