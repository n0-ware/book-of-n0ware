---
tags:
topic: "sec_network_arch"
subTopic: "net_device_attributes"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_net_device_attributes" 
cert: "Sec+"
---
# Network Device Attributes
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Attributes of network security devices play a crucial role in their placement within the network topology. Understanding these attributes helps in optimizing network security strategies.

## Active vs. Passive Controls
- **Passive Controls**: Operate without requiring client configuration or direct data exchange with hosts. They're undetectable by network hosts and do not have addressable interfaces. Example: traffic analysis by a sensor.
- **Active Controls**: Require configuration with credentials and permissions, and they exchange data with target hosts. This includes controls that filter traffic, necessitating host configuration to use the control as a gateway or installing agent software.

## Inline vs. Monitor Deployment
- **Inline Deployment**: Devices are part of the physical cable path, requiring no IP or routing topology changes. They're not configured with MAC or IP addresses and directly influence the traffic flow.
  - Example: TAP (Test Access Point), a physical device that copies signals from the network cabling to a monitor port, offering a reliable method to capture every frame.
- **Monitor Deployment**: Utilizes network features like SPAN (Switched Port Analyzer) or mirror ports to copy frames to a detection system. This method can be less reliable due to potential frame dropping under heavy load or errors.

## Fail-Open vs. Fail-Closed
- **Fail-Open**: In a device failure, network or host access is preserved. This approach prioritizes availability but poses a risk if a threat actor induces a failure to bypass the control.
- **Fail-Closed**: In a device failure, access is blocked or the system defaults to the most secure state. This approach prioritizes confidentiality and integrity but risks causing system downtime.

### Considerations for Fail Modes
- **Configuration**: Not all devices allow configuration of fail modes.
- **System Design**: Some inline appliances include backup paths for fail-open operation to maintain availability even in case of failure.
- **Risk Assessment**: Choosing between fail-open and fail-closed involves assessing the prioritization of availability versus security within the specific network context.

## Examples and Implications
- **Router/Firewall**: An active control requiring client devices to be configured for internet access.
- **TAP vs. Mirror Port**: TAPs offer a more reliable, inline method for traffic monitoring compared to SPAN ports, which may not capture all traffic due to errors or high load.

Understanding these device attributes and their implications on network security enables organizations to design more secure, resilient, and efficient network architectures that align with their specific security policies and operational requirements.
