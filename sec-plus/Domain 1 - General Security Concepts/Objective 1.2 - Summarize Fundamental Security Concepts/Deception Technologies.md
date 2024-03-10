---
tags:
topic: "sec_general"
subTopic: "deception_tech"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_deception_tech" 
cert: "Sec+"
---
# Deception Technologies
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Techniques that deceive and disrupt attackers, such as honeypots, honeynets, honeyfiles, and honeytokens are all tools used to detect, defend, and learn about attacks. 
- **Honeypots** are decoy systems that mimic real systems but allow security teams to monitor attacker activities and gather information. 
- **Honeynets** are networks of interconnected honeypots and are both extensive and realistic
- **Honeyfiles** are fake but appear to have real sensitive information and detect attempts to access and steal data. 
- **Honeytokens** are false creds or other data types used to distract attackers, trigger alerts, and offer insights. 

Some strategies include:
- Using bogus DNS entries to list nonexistant hosts
- Configuring web servers with multiple decoy directories or dynamic web pages to slow scanning
- Using port triggering or spoofing to return fake telemetry data when a host detects port scanning. This causes multiple ports to falsly report as open, slowing down the scan, or returning fake IP addresses
- Using DNS Sinkholes to route suspect traffic to a different network. 
	- A temporary DNS record that redirects malicious traffic to a controlled IP address.