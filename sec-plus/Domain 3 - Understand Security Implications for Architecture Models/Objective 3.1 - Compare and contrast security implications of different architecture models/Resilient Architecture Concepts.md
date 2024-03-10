---
tags:
topic: "sec_network_arch"
subTopic: "resilient_net_arch"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_resilient_net_arch" 
cert: "Sec+"
---
# Resilient Architecture Concepts
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## High Availability in Storage
- **Definition**: Storage provision with a guarantee of 99.99% uptime or better.
- **Redundancy**: Multiple disk controllers and storage devices available to ensure continuous availability.
- **Data Replication**: Across pools or groups supported by separate hardware resources.

## Data Replication
- **Purpose**: Copy data for effective utilization across business units.
- **Requirements**: Low latency network connections, security, and data integrity.
- **Performance Tiers**: Varying storage classes offered by CSPs.
- **Hot vs. Cold Storage**:
  - **Hot Storage**: Quick data retrieval but higher cost.
  - **Cold Storage**: Slower data retrieval, cost-effective.

## Application Replication Needs
- **Databases**: Require low-latency, synchronous replication.
- **Data File Replication**: Varies depending on data criticality.

## High Availability Across Zones and Regions
- **CSP Regions**: Independent areas divided into availability zones.
- **Advantages**: Lower latency services, increased redundancy and performance.
- **Multi-Zone/Region Provisioning**: Improves performance and redundancy but demands adequate replication performance.

## Replication Tiers Offered by CSPs
- **Local Replication**: Data replicated within a single datacenter; separate fault and upgrade domains.
- **Regional Replication (Zone-Redundant Storage)**: Data replicated across multiple datacenters within one or two regions, protecting against single datacenter outages.
- **Geo-Redundant Storage (GRS)**: Data replicated to a secondary, distant region, safeguarding against regional outages or disasters.

These resilient architecture concepts emphasize the importance of replication, redundancy, and strategic regional distribution in cloud computing to ensure high availability, data integrity, and disaster recovery.
