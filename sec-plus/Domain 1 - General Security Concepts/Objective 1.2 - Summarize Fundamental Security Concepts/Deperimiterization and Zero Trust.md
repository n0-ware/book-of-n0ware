---
tags:
topic: "sec_general"
subTopic: "zero_trust"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_zero_trust" 
cert: "Sec+"
---
# Deperimiterization and Zero Trust
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Deperimiterization

> A security approach focusing on shifting network defenses from the boundary of the network to individual resources on a network, which is crucial for cloud computing.

- Perimeter models are no longer effective. 
- Defense in depth never more important, including all assets such as data, apps, and services. 
- Relies on robust authentication, encryption, and access control
- Requires continue monitoring to maintain security on resources
- Cloud/hybrid workloads, remote workers, mobile devices, outsourcing and contracting, and WiFi all drive this

## Zero trust

> The security design paradigm where any request (host-to-host or container-to-container) must be authenticated before being allowed.
> Or from NIST: cybersecurity paradigms that move defenses from static, network-based perimeters to focus on users, assets, and resources.

**The assumption that all devices, users, and services have no inherent trust, regardless of location, requiring all devices and users to authenticate and be authorized before accessing network resources.**

- Nothing should be taken for granted
- All access to networks must be continuously verified and authenticated.
- All entities seeking access must be authenticated and verified. 
- Differs from traditional security models that grant permanent access once inside a trusted network or zone.

### Key Benefits to Zero Trust
- Great security through constant authentication and verification prior to and during access
- Better access controls, including time limits for access
- Improved governance and compliance through limited data access, ensuring that visibility is there when data is accessed.
- More granularity and more "least privilege"

### Fundamental Needs
- **Adaptive identity** which recognizes that user identities do not remain the same and ID verification needs to be continuous based on current context and the resources they are accessing.
- **Threat scope reduction** ensuring access to network resources is only granted on need-to-know for specific tasks, reducing potential damage anyone can cause. 
- **Policy-driven access control** ensures that technical controls exist to enforce access restrictions. 

> The "posture" of a device refers to its current security status, including configurations, patch levels, software, etc. In this context, posture assessments determine if access is permitted or if it poses a risk
### Essential Components
- Network/Endpoint security including control to apps, data, and networks
- IAM, ensuring only verified users
- Policy-based enforcement, specifically with network traffic
- Cloud security
- Network visibility through logging
- Network segmentation
- Data protection
- Threat detection and prevention

### Zero Trust Architecture

The control and data planes are implemented separately and have different functions. The goal of this design makes an implicit trust zone as small and brief as possible, down to the individual transaction if possible. This continues to separate your "place in the network" from your trust status. Separation of the two planes ensures consistency in application for access request handling across trusted, untrusted, and third-party networks, regardless of the device or trust location. Finally, continuous monitoring ensures that any anomalous behavior can be identified, and sessions terminated. 
#### Control Plane
> Manages policies taht decide how users and devices are authorized to access network resources, implemented through a central decision point. This point defines policies that limit access, monitor, and update policies. 
1. A policy engine is configured to enable dynamic and continuous authentication and authorization decisions
	1. Identities.
	2. Policies.
	3. Continuous security monitoring.
2. Policy administrator implements an interface for communicating policy decisions to the Data Plane's systems. 

**It is crucial that the only processes interacting with the policy administrator are those responsible for policy enforcement. A root of trust must be confidently and securely established.**
#### Data Plane

3. Subjects (users, etc.) have credentials
4. Subjects must use client systems to make requests, but the systems are not trusted.
5. A Policy Enforcement Point system is the only entity trusted to communicate requests and receive decisions from the Policy Administrator.
6. The Policy Enforcement Point implements encrypted session setup and tear down as directed.
7. Architecture creates a limited scope and duration "trust zone" for resource access.

![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/1_SecPlus_zero_trust.png]]