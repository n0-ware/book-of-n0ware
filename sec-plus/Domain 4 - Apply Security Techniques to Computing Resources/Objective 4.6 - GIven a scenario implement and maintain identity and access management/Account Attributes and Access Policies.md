---
tags:
topic: "sec_iam"
subTopic: "accounts"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_accounts" 
cert: "Sec+"
---
# Account Attributes and Access Policies
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Account Attributes
- **Unique Security Identifier (SID)**: A unique value used to identify a user account or group account within Windows environments.
- **Name and Credential**: Identifiers for account login and authentication.
- **Profile**: Stores custom identity attributes like full name, email, contact number, department, etc.
  - May include a user account picture.
  - Provides a location for user-generated data (home folder).
  - Stores per-account settings for software applications.

## Access Policies
- **Permissions**: Define access to files and network resources.
  - Can be assigned directly or inherited through security groups or roles.
- **Privileges**: Govern the use and configuration of network hosts, including:
  - Right to log on locally or via remote desktop.
  - Ability to install software.
  - Permission to change network configurations.
- **Group Policy Objects (GPOs) on Windows Active Directory**:
  - Used to configure access rights systematically.
  - Can be linked to Active Directory administrative boundaries (sites, domains, OUs).

## Management of GPOs
- **Purpose**: Provide centralized management of access policies and configurations across a Windows network.
- **Application**: Affects user/group/role accounts based on their association within the Active Directory structure.

## Best Practices
- **Detailed User Profiles**: Enhance security and user management by accurately reflecting each user's role and needs.
- **Role-Based Access Control (RBAC)**: Simplifies permissions management by assigning access based on roles rather than individual attributes.
- **Effective Use of GPOs**: Ensures consistent access policies and reduces administrative overhead.
- **Regular Audits**: Maintain security by periodically reviewing account attributes, group memberships, and access rights.
