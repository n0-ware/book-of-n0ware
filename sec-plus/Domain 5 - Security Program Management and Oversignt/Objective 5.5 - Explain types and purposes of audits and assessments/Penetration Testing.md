---
tags:
topic: "sec_grc"
subTopic: "assessments"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_assessments" 
cert: "Sec+"
---
# Penetration Testing
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

- Uses authorized hacking techniques to discover security weaknesses.
- Also known as ethical hacking.
- Involves steps like verifying threats, bypassing security controls, testing security controls, and exploiting vulnerabilities.
- Active testing of security controls differentiates it from passive vulnerability assessment.
- Active testing aims to actively exploit vulnerabilities.

## Active and Passive Reconnaissance

- Active reconnaissance involves probing and interacting with target systems to gather information.
- Techniques include port scanning, service enumeration, OS fingerprinting, DNS enumeration, and web application crawling.
- Passive reconnaissance gathers information without directly interacting with targets, using sources like OSINT, network traffic analysis, and social engineering.

## Known, Partially Known, and Unknown Testing Methods

- Known Environment Penetration Testing: Detailed knowledge of the target system or network.
- Partially Known Environment Penetration Testing: Limited knowledge, requiring reconnaissance to gather additional information.
- Unknown Environment Penetration Testing: Little to no prior knowledge, simulating an attacker with no preexisting information.

## Offensive and Defensive Penetration Testing

- **Offensive Penetration Testing (Red Teaming):**
    - Simulates real-world cyberattacks to identify vulnerabilities and potential attack vectors.
    - Mimics tactics, techniques, and procedures of potential attackers.
- **Defensive Penetration Testing (Blue Teaming):**
    - Evaluates defensive security measures, detection capabilities, and incident response procedures.
    - Assesses the effectiveness of existing security controls and identifies areas for improvement.

## Physical Penetration Testing

- **Physical Security Testing:**
    - Assesses physical security practices and controls.
    - Simulates real-world attack scenarios to identify vulnerabilities in access controls, surveillance, and perimeter defenses.
    - Tests for unauthorized physical access using techniques like social engineering, tailgating, and lock picking.

## Integrated Penetration Testing

- **Integrated Penetration Testing:**
    - Holistic approach combining different penetration testing methodologies and techniques.
    - Assess the overall security of systems, networks, applications, and physical infrastructure.
    - Provides a comprehensive evaluation of security operations by combining offensive and defensive testing approaches.

## Continuous Penetration Testing

- **Continuous Penetration Testing:**
    - Focuses on technical vulnerabilities and is often configured for automation, especially in CI/CD environments.
    - Provides ongoing monitoring and assessment of security posture.
    - Helps identify and remediate vulnerabilities in real-time to improve security resilience.