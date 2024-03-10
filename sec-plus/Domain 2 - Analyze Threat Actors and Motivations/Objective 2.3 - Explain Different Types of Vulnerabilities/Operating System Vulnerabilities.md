---
tags: 
topic: sec_threats_vulns_risk
subTopic: os_vulns
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_os_vulns
cert: Sec+
---
# Operating System Vulnerabilities
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`



## General Importance
- **Significance**: OS vulnerabilities can lead to major issues like malware installation, data theft, and unauthorized access.

## Microsoft Windows
- **Characteristics**: Extensive features, wide user base, especially in corporations and governments.
- **Common Vulnerabilities**: Buffer overflows, input validation issues, privilege flaws.
- **Impact**: Targeted due to its large install base and critical use in large organizations.

## Apple macOS
- **Base**: UNIX-based architecture.
- **Weaknesses**: Access controls, secure boot processes, third-party software.
- **User Base and Perception**: Smaller than Windows but growing; often seen as safer, leading to complacency.

## Linux
- **Usage**: Popular in servers, desktops, and mobile.
- **Nature**: Open-source with rapid development and vulnerability repair.
- **Issues**: Kernel vulnerabilities, misconfigurations, unpatched systems.
- **Relevance**: Widespread use in cloud and server infrastructure.

## Mobile Operating Systems (Android and iOS)
- **Trends**: Increasing use as primary computing platforms.
- **Android**: Open source, fragmented across manufacturers, inconsistent in patching.
- **iOS**: Closed source, still impacted by significant vulnerabilities.
## Embedded Systems (IoT)
- **Growth**: Introduction of IoT adds to the array of specialty OS vulnerabilities.
- **Risk**: Potential pathways into corporate infrastructures.
## Example OS Vulnerabilities
- **Microsoft Windows**:
  - **MS08-067**: Remote code execution vulnerability, exploited by Conficker worm.
  - **MS17-010/EternalBlue**: SMB protocol vulnerabilities, leveraged in WannaCry ransomware attack.
- **macOS**:
  - **Shellshock (2014)**: Bash shell flaw affecting Unix-based systems, including macOS.
- **Android**:
  - **Stagefright (2015)**: Vulnerability in media library allowing code execution via MMS messages.
- **iOS**:
  - **Project Zero (2019)**: Series of vulnerabilities exploited in "watering hole" attacks.
- **Linux**:
  - **Heartbleed (2014)**: Bug in OpenSSL cryptographic software, compromising secret keys.
