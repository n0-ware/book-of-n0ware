---
tags:
topic: "sec_web"
subTopic: "dns"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_dns" 
cert: "Sec+"
---
# DNS Filtering
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# DNS Filtering and Security

DNS filtering is a critical cybersecurity measure that blocks access to malicious or inappropriate websites by controlling domain name resolution. It's a proactive defense mechanism that enhances organizational security policies and protects all network-connected devices.

## Implementing DNS Filtering

- **DNS Filtering Services**: Utilize services like Cisco's OpenDNS, Quad9, or CleanBrowsing for built-in filtering with external DNS resolution.
- **Own DNS Servers**: For organizations managing DNS servers (e.g., Microsoft DNS, BIND), direct implementation allows full control over filtering policies.
- **DNS Firewalls**: Intercept DNS queries at the network level to apply filtering rules.
- **Endpoint Protection Tools**: Offer DNS filtering capabilities for individual devices, ideal for mobile devices.
- **Pi-hole and ADGuard**: Open-source solutions for local DNS resolution with filtering, often deployed on low-cost hardware like Raspberry Pi.

Customization and regular updates of filtering policies are essential to maintain effectiveness against evolving threats.

## DNS Security

- **Fault Tolerance and DoS Attack Protection**: Local DNS servers should limit recursive queries to authenticated local hosts and implement access control to prevent unauthorized alterations.
- **Software Vulnerabilities**: Regularly update DNS server software (e.g., BIND, Microsoft DNS) to patch known vulnerabilities.
- **DNS Footprinting Mitigation**: Apply access control lists to prevent unauthorized zone transfers and protect network architecture information.
- **DNSSEC (DNS Security Extensions)**: Mitigates spoofing and poisoning attacks by validating DNS response authenticity, establishing a chain of trust from root servers to subdomains.

DNS filtering and security practices are foundational to safeguarding an organization's network, requiring diligent management and updates to adapt to new threats and compliance requirements.
