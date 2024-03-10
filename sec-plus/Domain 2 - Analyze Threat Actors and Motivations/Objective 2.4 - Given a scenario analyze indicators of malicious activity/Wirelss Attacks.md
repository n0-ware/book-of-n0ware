---
tags:
topic: ""
subTopic: "wireless_attacks"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_wireless_attacks" 
cert: "Sec+"
---
# Wirelss Attacks
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
Wireless networks are susceptible to specific security challenges and attacks due to their nature.

## Rogue Access Points
- **Definition**: Unauthorized access points installed on a network.
- **Types**:
  - **Malicious Intent**: Set up to create backdoors in the network.
  - **Accidental Creation**: Non-malicious users accidentally enabling unauthorized access points.
- **Evil Twin Attacks**:
  - **Concept**: Rogue access points masquerading as legitimate ones.
  - **Techniques**: Typosquatting, SSID stripping, DoS to overpower legitimate access points.
  - **Risks**: Harvesting user credentials, on-path attacks like DNS redirection.
- **Detection**:
  - **Physical Inspections**: Identifying unauthorized hardware.
  - **Wi-Fi Analyzers and Wireless Intrusion Systems**: Detecting rogue SSIDs, spoofed MAC addresses.

## Wireless Denial of Service (DoS) Attacks
- **Objective**: Prevent clients from connecting to legitimate access points.
- **Methods**:
  - **Interference**: Using other radio sources or rogue access points to jam signals.
  - **Disassociation Attacks**: Exploiting unencrypted management frames to disconnect clients.

## Wireless Replay and Key Recovery
- **Vulnerabilities**: Wireless authentication susceptible to replay attacks.
- **KRACK Attack**:
  - **Target**: WPA and WPA2 4-way handshake.
  - **Method**: Capturing authentication hashes for offline cracking.
  - **Prevention**: Ensuring clients and access points are fully patched.

Wireless networks require specific security measures to mitigate these unique risks, including monitoring for rogue access points, securing access point configurations, and staying vigilant against DoS and replay attacks.
