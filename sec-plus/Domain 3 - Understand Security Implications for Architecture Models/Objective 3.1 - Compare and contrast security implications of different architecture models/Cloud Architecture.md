---
tags:
topic: "sec_network_arch"
subTopic: "cloud_arch"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_cloud_arch" 
cert: "Sec+"
---
# Cloud Architecture
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Serverless Computing
- **Model**: Cloud provider manages infrastructure, automatically allocating resources as needed.
- **Billing**: Based on actual usage, not fixed server capacity.
- **Examples of Applications**: Chatbots, mobile backends, event-driven processing.
- **Providers**: Amazon Web Services (AWS) Lambda, Google Cloud Functions, Microsoft Azure Functions.
- **Advantages**:
  - Scalability and cost-effectiveness.
  - Reduced management effort for servers, software, and patches.
  - Event-driven orchestration for operations.
- **Network Security**: Emphasis on client security, with infrastructure managed by the service provider.
- **Design Logic**: Focuses on functions and microservices rather than monolithic server environments.

## Microservices
- **Approach**: Building applications as a collection of small, independent services.
- **Characteristics**: Modular design, well-defined interfaces, single responsibilities.
- **Benefits**: Efficient development, independent scaling, and updating of components.
- **Integration Challenges**: Potential issues during the integration of individual components.
- **Relation to Infrastructure as Code (IaC)**: Often implemented using IaC practices for efficient infrastructure deployment.

## Transformational Changes in Cloud Computing
- **Unique Architectural Services**:
  - **Elastic Compute and Auto-Scaling**: Dynamic adjustment of computing power based on demand.
  - **Advanced CDN**: Optimizing web traffic and content caching.
  - **Object Storage**: Massive, unstructured data storage services.
  - **Identity and Access Management**: Advanced security and integration tools.
  - **Containerization and Orchestration**: Changing application deployment and management.
  - **AI and Machine Learning Services**: Expanding capabilities for data analysis and automation.
  - **Serverless Databases and IoT Services**: Offering new back-end solutions.
- **Impact**: Enables scalability, innovation, and operational optimization.
- **Security Risks**: New security challenges and potential for significant data breaches.

Cloud architecture encompasses a range of services and models, each with its own set of benefits and challenges, fundamentally transforming how organizations build, deploy, and manage applications and infrastructure.
