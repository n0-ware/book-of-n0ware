---
tags:
topic: "sec_iam"
subTopic: "access_control"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_access_control" 
cert: "Sec+"
---
# Discretionary and Mandatory Access Control
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Discretionary Access Control (DAC)
- **Principle**: Based on the ownership of resources.
- **Ownership**: Each resource has an owner who controls access.
- **Access Control List (ACL)**: Owners modify ACLs to grant rights to others.
- **Flexibility**: DAC is the most flexible access control model.
- **Implementation**: Widely used in UNIX/Linux and Microsoft Windows file systems.
- **Weaknesses**:
  - Difficult to enforce centralized security policies.
  - Vulnerable to insider threats and compromised accounts.

## Mandatory Access Control (MAC)
- **Principle**: Based on security clearance levels.
- **Classification and Clearance**:
  - Objects are labeled with a classification.
  - Subjects are granted clearance levels to access objects.
- **Access Rules**:
  - Subjects can read objects at their clearance level or below (e.g., Top Secret can access Secret and Confidential).
  - Write up, read down policy restricts writing to higher classified documents.
- **Compartment-Based Access**: Adds flexibility by combining classification labels with specific compartments.
- **Non-Discretionary Rules**: Rules are established and cannot be changed by users.

## Differences Between DAC and MAC
- **Control Over Access**:
  - DAC allows resource owners to control access.
  - MAC uses a centralized policy that restricts access based on classification and clearance.
- **Flexibility vs. Security**:
  - DAC offers more flexibility but is less secure due to vulnerability to insider threats.
  - MAC is more secure by enforcing strict access control rules but is less flexible.
- **Use Cases**:
  - DAC is suitable for environments where user control over resources is prioritized.
  - MAC is preferred in high-security environments requiring strict access control based on classification levels.
