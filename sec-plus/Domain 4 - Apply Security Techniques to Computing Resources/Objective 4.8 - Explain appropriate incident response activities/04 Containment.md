---
tags:
topic: "sec_ir"
subTopic: "containment"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_containment" 
cert: "Sec+"
---
# Containment
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Determining an Appropriate Response

- The incident management database contains event indicators, incident details, impact assessment, and the responsible investigator.
- Containment is the phase where an appropriate response is determined.

## Complex Considerations

- Incidents vary in terms of scenarios, motivations, technologies, and seriousness.
- Key considerations include assessing existing damage, countermeasures, avoiding alerting threat actors, and preserving evidence.
- Notification and reporting requirements must be considered at this stage.

## Isolation-Based Containment

- Isolation involves removing an affected component from its larger environment.
- Options include disconnecting a host from the network, isolating infected VLANs, using firewalls, or disabling user accounts or application services.
- Temporarily disabling user accounts can prevent further damage by intruders.

## Segmentation-Based Containment

- Segmentation uses network technologies like VLANs, routing/subnets, and firewall ACLs to isolate hosts.
- It prevents communication outside the protected segment.
- A protected segment can be configured as a sinkhole or honeynet to deceive attackers and facilitate threat analysis.

