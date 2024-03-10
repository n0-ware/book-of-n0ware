---
tags: 
topic: sec_iam
subTopic: access_control
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_rbac_abac
cert: Sec+
---
# Access Control Schemes
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Role-Based Access Control (RBAC)
- **Definition**: Permissions are defined by roles corresponding to the tasks an employee or service must perform.
- **Roles**: Each set of permissions is encapsulated in a role assigned to users or service accounts.
- **Nondiscretionary System**: Rights to modify role permissions are reserved to a system owner, making it rules-based.
- **Implicit Rights**: Principals gain rights through role assignment rather than direct permission allocation.
- **Security Group Accounts**:
  - Provides a way to approximate RBAC in discretionary systems.
  - Rights are assigned to groups, and users gain rights by group membership.
- **Differences from Security Groups**:
  - Security group membership is more discretionary, managed by administrators.
  - RBAC aims for roles to provide permissions needed for specific tasks, ideally temporarily.

## Attribute-Based Access Control (ABAC)
- **Definition**: Access decisions are based on a combination of subject and object attributes, along with contextual or system-wide attributes.
- **Attributes**: Can include group/role memberships, OS details, IP addresses, patch levels, antimalware presence, and more.
- **Context-Sensitive Decisions**:
  - Monitors events or alerts associated with user accounts or resources.
  - Ensures access requests are consistent in terms of timing or geographic location.
- **Policies Implementation**:
  - Supports complex policies like M-of-N control and separation of duties.

## Comparing RBAC and ABAC
- **Flexibility**:
  - RBAC provides structured access control based on organizational roles, simplifying management but potentially limiting flexibility.
  - ABAC offers fine-grained access control, allowing for more dynamic and context-aware policies.
- **Implementation**:
  - RBAC is easier to implement and manage in environments with well-defined roles and responsibilities.
  - ABAC requires more sophisticated systems to evaluate attributes and contexts, making it more complex but adaptable to changing requirements.
- **Use Cases**:
  - RBAC is suited for environments where access needs are well understood and relatively static.
  - ABAC is beneficial in environments requiring adaptive security measures based on real-time data and varying contexts.

# Rule-Based Access Control

## Definition
- **Rule-Based Access Control**: Access control policies are determined by system-enforced rules, not by user discretion.
- **Nature**: Considered nondiscretionary, as it restricts access based on predefined rules set by the system or administrators.

## Examples of Rule-Based Access Control
- **Role-Based Access Control (RBAC)**: Access based on roles within an organization.
- **Attribute-Based Access Control (ABAC)**: Access determined by attributes of users, devices, or environment.
- **Mandatory Access Control (MAC)**: Access control based on security clearance levels and classification labels.

## Conditional Access
- **Description**: Monitors account or device behavior; access can be modified based on certain conditions.
- **Actions**: May suspend accounts or require reauthentication if specific conditions are met.
- **Authentication**: Often involves two-step verification for additional security.

## Implementations of Conditional Access
- **User Account Control (UAC)**: Windows feature that prompts users for confirmation or additional authentication for actions requiring elevated privileges.
- **sudo Restrictions**: In UNIX/Linux, restricts access to privileged commands, requiring user authentication.
- **Role-Based Rights Management and ABAC**: Can incorporate various criteria for conditional access, such as location-based policies.

## Characteristics
- **System-Enforced**: Rules are applied automatically by the system, reducing the risk of unauthorized access.
- **Flexibility**: Can be adapted to various security needs, from simple role assignments to complex attribute evaluations.
- **Security Enhancement**: Helps in preventing unauthorized actions by enforcing strict access rules based on predefined policies.
