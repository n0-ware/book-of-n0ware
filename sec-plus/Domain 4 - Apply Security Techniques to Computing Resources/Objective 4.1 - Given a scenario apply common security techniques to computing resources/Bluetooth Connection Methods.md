---
tags:
topic: "sec_mobile"
subTopic: "bluetooth"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_bluetooth" 
cert: "Sec+"
---
# Bluetooth Connection Methods
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Security Issues

- **Device Discovery**:
  - Devices can be detected even in non-discoverable mode.
- **Authentication and Authorization**:
  - Use secure phrases for device pairing to prevent unauthorized access.
  - Regularly review device pairing lists.
- **Malware**:
  - Vulnerabilities like BlueBorne allow system compromise without user interaction.
  - Keep devices updated to mitigate risks.

## Risks

- **Bluejacking**:
  - Unsolicited messages or contacts sent to your device, potential malware vector.
- **Bluesnarfing**:
  - Exploit to steal information; mitigated by patched vulnerabilities and secure PINs.
- **Peripheral Device Connections**:
  - Risk of attacks from peripherals with malicious firmware, though low likelihood.

## Bluetooth Security Features

- **Pairing and Authentication**:
  - Devices exchange cryptographic keys for secure communication.
  - Various methods like numeric comparison, passkey entry, or OOB authentication.
- **Bluetooth Permissions**:
  - User consent required for connections and service access.
  - Manageable permissions to prevent unauthorized access.
- **Encryption**:
  - Protects data transmitted between devices using a shared secret key.
- **Bluetooth Secure Connections (BSC)**:
  - Increases resistance against eavesdropping and unauthorized access, introduced in Bluetooth 4.0.
- **Bluetooth Low Energy (BLE) Privacy**:
  - Uses randomly generated addresses that change periodically to prevent device tracking.
