---
tags: 
topic: sec_mobile
subTopic: encryption
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_encryption
cert: Sec+
---
# Full Device Encryption and External Media
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Full Device Encryption

- **Availability**: Present in all but early versions of smartphone and tablet OSes.
- **iOS Encryption**:
  - User data always encrypted, with the key stored on the device.
  - "Data Protection" option adds a second encryption layer for email and apps, using a key derived from the user's credential.
  - Not all data is covered by "Data Protection" (e.g., contacts, SMS, pictures).
  - Enabled automatically with password lock.
- **Android Encryption**:
  - Differences in encryption options across versions.
  - As of Android 10, file-level encryption is used by default, not full disk encryption, due to performance concerns.

## External Media

- **Storage Options**:
  - Mobile devices use solid state drives for storage.
  - Some Android devices support removable storage (e.g., MicroSD) and USB storage connections.
- **Encryption Concerns**:
  - OS encryption may not cover removable storage.
  - Use third-party software for encryption of removable storage recommended.
  - Limit sensitive data on removable storage due to security risks.

## MicroSD HSM

- A small hardware security module for storing cryptographic keys.
- Enables use of cryptographic material across different devices (e.g., laptops, smartphones).
