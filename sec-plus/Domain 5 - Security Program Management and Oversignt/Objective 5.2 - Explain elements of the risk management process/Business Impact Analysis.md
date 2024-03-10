---
tags:
topic: "sec_grc"
subTopic: "bia"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_bia" 
cert: "Sec+"
---
# Business Impact Analysis
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Identification of Critical Systems

- To ensure resiliency of mission essential and primary business functions, identify critical systems.
- Asset types include people, tangible assets, intangible assets, and procedures.
- Reduce dependencies between components supporting mission essential functions.

## Business Impact Analysis (BIA)

- BIA helps businesses understand the potential effects of disruptions on their operations.
- Identify and assess the impact of unplanned threat scenarios (e.g., accidents, emergencies, disasters).
- Quantify losses and assess the worthiness of security controls (e.g., DDoS attack impact assessment).

## Mission Essential Functions (MEF)

- MEFs are functions that cannot be deferred and must be performed continually.
- Restore MEFs first in case of service disruption.
- Analyzed using metrics like Maximum Tolerable Downtime (MTD), Recovery Time Objective (RTO), Work Recovery Time (WRT), and Recovery Point Objective (RPO).

### Metrics Governing Mission Essential Functions

- **Maximum Tolerable Downtime (MTD)**: Longest period a business function outage can occur without causing irrecoverable failure.

- **Recovery Time Objective (RTO)**: Period following a disaster when an IT system may remain offline.

- **Work Recovery Time (WRT)**: Time to reintegrate systems, test functionality, and brief users after recovery.

- **Recovery Point Objective (RPO)**: Amount of data loss a system can sustain.

## MTD and RPO Impact

- MTD and RPO help determine critical business functions and appropriate risk countermeasures.
- Impact the frequency of data backups, data replication requirements, and recovery solutions.

## Mean Time to Repair (MTTR) and Mean Time Between Failures (MTBF)

- Key performance indicators (KPIs) for measuring reliability and efficiency of systems.
- MTBF represents expected product lifetime, calculated as total operational time divided by failures.
- MTTR measures time to correct a fault and restore full system operation.
- Lower MTTR indicates quicker restoration, reducing downtime and disruptions.
- Higher MTBF suggests greater reliability and longer intervals between failures, impacting maintenance and system performance decisions.

