---
tags:
topic: "sec_network_arch"
subTopic: "net_attack_surface"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_net_attack_surface" 
cert: "Sec+"
---
# Network Attack Surface
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

The network attack surface comprises all potential points through which a threat actor can gain unauthorized access to hosts and services. Understanding and mitigating the attack surface requires a layered approach.

## Layer Model Analysis for Attack Surface
- **Layer 1/2**: Risks involve unauthorized connections to physical ports or wireless networks, enabling communication within the same broadcast domain.
- **Layer 3**: Threats include unauthorized acquisition of valid network addresses, possibly through spoofing, to communicate across zones.
- **Layer 4/7**: Vulnerabilities allow unauthorized connections to TCP or UDP ports, facilitating interaction with application layer protocols and services.

## External vs. Internal Attack Surface
- Distinguishing between external/public and internal/private attack surfaces is crucial for applying appropriate security measures.

## Defense in Depth
- Implementing multiple layers of security controls (defense in depth) is essential to prevent, detect, and correct attacks.
- Security controls at the network perimeter aim to block external attacks, while internal segregation and zoning mitigate risks from compromised or unauthorized internal hosts.

## Typical Network Architecture Weaknesses
- **Single Points of Failure**: Reliance on a single server, appliance, or network channel increases vulnerability to service disruptions.
- **Complex Dependencies**: Systems requiring numerous other systems for functionality are more susceptible to service failures.
- **Prioritizing Availability Over Security**: Compromising security for quick service deployment creates long-term risks.
- **Lack of Documentation and Change Control**: Undocumented changes can lead to a poorly understood network structure, complicating security efforts.
- **Overdependence on Perimeter Security**: A "flat" network architecture without sufficient internal segmentation offers attackers greater mobility once the perimeter is breached.

## Security Control Strategies
- Employing a combination of preventive, detective, and corrective measures tailored to each layer of the network.
- Rigorous change control procedures and thorough documentation to maintain visibility and control over network architecture.
- Implementing segmentation and zoning within the network to limit movement and access for unauthorized or compromised hosts.

Understanding the network attack surface and employing a multi-layered security approach are fundamental to safeguarding network integrity and ensuring the confidentiality, availability, and integrity of data and services.
