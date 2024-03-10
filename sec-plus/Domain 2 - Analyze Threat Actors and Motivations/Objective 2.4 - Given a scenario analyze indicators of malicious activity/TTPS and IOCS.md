---
tags: 
topic: sec_threats_vulns_risk
subTopic: ttps_iocs
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_ttps_iocs
cert: Sec+
---
# TTPS and IOCS
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# TTPs AND IOCs

## Antivirus (A-V) Scanners
- **Function**: Recognize known malware code through signature-based detection.
- **Process**: Scans files against a continually updated database of malware signatures.
- **Limitation**: Less effective against sophisticated attacks not based on known malware.

## TTP Analysis
- **Tactic**: High-level description of threat behavior (e.g., reconnaissance, persistence).
- **Technique**: How a threat actor carries out a tactic (e.g., network scanning, vulnerability scanning).
- **Procedure**: Detailed execution of a technique (e.g., specific tools or methods used).

### Example
- **Scenario**: A criminal gang uses ransomware to blackmail companies.
- **Tactics**: Includes reconnaissance, resource development, initial access, and execution.
- **Techniques and Procedures**: Novel exploitation methods for initial access, detailed malware execution strategies.

## Indicators of Compromise (IoC)
- **Definition**: Signs that indicate a successful attack or ongoing attack.
- **Examples**: Compromised processes, connections to C&C networks, registry changes, encrypted files, ransom notes.
- **Variability**: Can range from definite signs like malware signatures to patterns requiring correlation of multiple data points.

## IoCs and Modern Scanning Tools
- **Integration**: Modern tools integrate threat feeds of published TTPs and IoCs.
- **Advantage**: Allows automated scanning for malicious behaviors beyond signature detection.

## Artificial Intelligence in Threat Intelligence
- **Usage**: AI systems analyze patterns of anomalous activity to identify IoCs.
- **Benefit**: Enables faster and more accurate detection and response.

## Indicator of Attack (IoA)
- **Definition**: Evidence of an intrusion attempt in progress.
- **Differentiation**: Focuses on attempts rather than successful attacks.

Understanding and effectively utilizing TTPs and IoCs are crucial for modern cybersecurity strategies. They enable organizations to detect a wider range of malicious activities and respond to them more efficiently, enhancing overall security posture.
