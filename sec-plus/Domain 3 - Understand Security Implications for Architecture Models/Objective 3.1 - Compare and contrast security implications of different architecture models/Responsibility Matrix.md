---
tags:
topic: "sec_network_arch"
subTopic: "cloud_responsibility_matrix"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_cloud_responsibility_matrix" 
cert: "Sec+"
---
# Responsibility Matrix
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Overview
- **Concept**: Security risks in cloud infrastructure are shared between the cloud provider and the customer.
- **Provider's Role**: Secures the underlying infrastructure.
- **Customer's Role**: Secures their applications and data.

## Division of Responsibility
- **SaaS, PaaS, IaaS Models**: The level of responsibility varies based on the service model.
- **Example**: In SaaS, the CSP handles operating system configuration; in IaaS, it's a shared responsibility.

## Responsibility Matrix
- **Function as a Service (FaaS)**: Part of serverless computing, scaling dynamically to handle load changes.

## Responsibilities of Cloud Service Provider
- Physical security of infrastructure.
- Securing computer, storage, and network equipment.
- Foundational networking elements, including DDoS protection.
- Cloud storage backup and recovery.
- Resource isolation security among tenants.
- Tenant resource identity and access control.
- Security monitoring and incident response.
- Managing geographically distributed datacenters.

## Responsibilities of Cloud Service Customer
- User identity management.
- Data and service geographic location configuration.
- Access controls to cloud resources.
- Data and application security configuration.
- Operating system protection, if deployed.
- Encryption use and key protection configuration.

## Importance of Customer Involvement
- **Active Management**: Implementing and managing security controls is an active process.
- **Boundary Identification**: Crucial to identify the security responsibility boundaries between the customer and the CSP.

The shared responsibility model emphasizes that while cloud providers offer robust security features, customers must also actively manage and secure their applications, data, and operating systems in the cloud environment.


![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_cloud_responsibility_matrix_1.png]]