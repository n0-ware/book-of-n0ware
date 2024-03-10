---
tags:
topic: "sec_iam"
subTopic: "accounts"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_accounts" 
cert: "Sec+"
---
# Account Restrictions
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Location-Based Policies
- **Network Location Identification**:
  - Utilizes IP address, subnet, VLAN, or OU.
  - Can restrict account access to specific network areas or servers.
- **Geographical Location Determination**:
  - **IP Address**: Approximates location based on ISP information. Accuracy varies by ISP's service area.
  - **Location Services**: Calculates precise location using GPS, triangulation with cell towers, Wi-Fi hotspots, and Bluetooth signals.

## Time-Based Restrictions
1. **Time-of-Day Restrictions**:
   - Defines authorized login hours for an account.
2. **Duration-Based Login**:
   - Sets a maximum session duration for logins.
3. **Impossible Travel/ Risky Login**:
   - Monitors login locations over time to detect and react to physically impossible travel scenarios, disabling accounts or raising alerts.
4. **Temporary Permissions**:
   - Automatically removes an account from a security role or group after a specified period.

## Implementation Methods
- **IP Geolocation**:
  - Software libraries like GeoIP query registrant-published data for IP address location approximation.
- **OS Location Services**:
  - Use built-in GPS sensors or network triangulation methods to determine device location.

## Security Applications
- **Enhanced Access Control**:
  - Tailors account access permissions based on the user's or device's physical or network location.
- **Prevention of Unauthorized Access**:
  - Blocks logins at unusual times or from geographically implausible locations.
- **Dynamic Permission Management**:
  - Adapts user rights and access levels based on temporal conditions or geographical factors.

## Best Practices
- **Regular Policy Review**: Ensure location and time-based policies remain relevant to organizational needs and security posture.
- **Integration with Existing Security Measures**: Combine with other security controls like multi-factor authentication (MFA) for comprehensive protection.
- **Alerting and Monitoring**: Implement systems to alert on policy violations or suspicious activities, facilitating rapid response.
