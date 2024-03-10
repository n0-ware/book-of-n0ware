---
tags: 
topic: sec_resilience
subTopic: advanced_data_protection
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_advanced_data_protection
cert: Sec+
---
# Advanced Data Protection
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Snapshots are critical in data protection, capturing a system's state at a specific point in time. They come in three main types:

- **VM Snapshots:** Capture the complete state of a virtual machine, including memory, storage, and settings. Useful for rolling back changes in case of failures or during testing.
- **Filesystem Snapshots:** Capture the state of a file system at a particular moment, allowing for file recovery or restoration to previous versions.
- **SAN Snapshots:** Block-level snapshots within a storage area network that capture the entire storage volume, enabling rapid recovery of datasets and applications.

### Replication and Journaling
Replication and journaling enhance data protection by maintaining multiple data copies and tracking changes:

- **Replication:** Involves creating exact data copies on different storage systems or locations, safeguarding against hardware failures or attacks.
- **Journaling:** Records data changes in a journal, allowing for tracking, monitoring modifications, and reverting to previous states if necessary.

### Encrypting Backups
Encrypting backups is vital for data security, privacy, and compliance:

- Ensures sensitive data in backups remains unreadable without the decryption key, protecting against unauthorized access or theft.
- Helps organizations meet regulatory requirements and avoid consequences of noncompliance.
