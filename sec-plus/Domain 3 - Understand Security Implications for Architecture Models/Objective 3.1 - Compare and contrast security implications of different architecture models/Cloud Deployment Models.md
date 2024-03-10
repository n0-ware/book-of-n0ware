---
tags:
topic: "sec_network_arch"
subTopic: "cloud_models"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_cloud_models" 
cert: "Sec+"
---
# Cloud Deployment Models
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Types of Cloud Deployment Models
- **Public (Multi-tenant)**: Offered over the Internet, shared resource with risks in performance and security.
- **Hosted Private**: Exclusively used by one organization, hosted by a third party, offers better security but is more expensive.
- **Private**: Owned and operated by the organization, greater control over privacy and security, suited for banking and governmental services.
- **Community**: Shared by several organizations with common concerns, like standardization and security policies.
- **Hybrid**: Combines public/private/community/hosted/on-site/off-site solutions for flexibility.

## Security Considerations for Different Architectures
- **Single-Tenant Architecture**: High security with dedicated infrastructure but more expensive and self-managed.
- **Multi-Tenant Architecture**: Cost-effective but increases risks of unauthorized access or data leakage.
- **Hybrid Architecture**: Offers flexibility and control over sensitive data but requires careful management for security.
- **Serverless Architecture**: Potentially more secure, as infrastructure is managed by the provider, but application and data access still need securing.

## Hybrid Cloud
- **Combination**: Mixes public and private clouds for flexibility, scalability, and cost savings.
- **Benefits**: Leverages both private (security/control) and public (cost-effective scalability) cloud advantages.
- **Security Challenges**: Managing multiple environments, integrating with on-premises infrastructure, and enforcing consistent security policies.
- **Data Redundancy and Protection**: Offers redundancy but can lead to data consistency issues.
- **Legal Compliance**: Ensuring data compliance in both on-premises and cloud components.
- **Service-Level Agreements (SLAs)**: Formalizing performance and support expectations, challenging with integrated systems.
- **Network Latency and Monitoring**: Increased complexity due to data transfers and specialized monitoring requirements.

These models highlight the need for careful consideration of security, performance, cost, and compliance when selecting and managing cloud environments.
