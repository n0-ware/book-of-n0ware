---
tags: 
topic: sec_threats_vulns_risk
subTopic: supply_chain_vulns
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_supply_chain_vulns
cert: Sec+
---
# Supply Chain Attacks
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
- **Description**: Risks and weaknesses introduced in software products during development, distribution, and maintenance stages.

## Service Providers
- **Role**: Offer development, testing, and deployment platforms.
- **Risks**: Inadequate security measures or insecure communication with other supply chain elements.

## Hardware Suppliers
- **Impact**: Crucial in the software supply chain, potential sources of vulnerabilities.
- **Issues**: Compromised hardware can lead to severe security breaches, especially in firmware or drivers.
- **Examples**: Preinstalled firmware vulnerabilities, susceptibility to physical tampering, outdated or unreliable drivers.

## Software Providers
- **Significance**: Providers of libraries, frameworks, and other third-party components.
- **Vulnerabilities**: Outdated or vulnerable third-party components expose applications to attacks.
- **Trust Factor**: Security depends on each provider maintaining high standards.

## Software Bill of Materials (SBOM)
- **Purpose**: Inventory of all components in a software product, including dependencies.
- **Benefits**: Enhances transparency, aids in vulnerability identification, and tracks component origins.
- **Use in Incident Response**: Facilitates rapid response to vulnerabilities in specific components.

## Dependency Analysis and SBOM Tools
- **OWASP Dependency-Check**: Identifies dependencies and associated vulnerabilities.
- **Functionality**: Generates reports listing libraries, components, and known vulnerabilities.
- **Limitations**: Primarily detects outdated/vulnerable components, may not include all SBOM information.
- **Comprehensive SBOM Tools**: Use output from Dependency-Check or follow SPDX or CycloneDX standards for more detailed information.

The software supply chain encompasses various entities and stages, each contributing to the overall security posture of the final product. Understanding and managing these vulnerabilities through tools like SBOMs and dependency analysis is crucial for maintaining software integrity and security.
