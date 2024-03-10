---
tags:
topic: "sec_wireless"
subTopic: "wireless_encryption"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_wireless_encryption" 
cert: "Sec+"
---
# Wireless Encryption
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Wi-Fi Protected Access (WPA)
- **Initial Version**: Designed to address vulnerabilities in the WEP standard.
- **Features**:
  - Uses RC4 stream cipher with Temporal Key Integrity Protocol (TKIP) for enhanced security.
  - TKIP adds mechanisms to strengthen encryption.

## Wi-Fi Protected Setup (WPS)
- **Purpose**: Simplifies secure access point setup for residential consumers.
- **Process**:
  - Utilizes a push-button or PIN method for easy setup.
  - Automatically generates a random SSID and PSK.
- **Vulnerability**:
  - Susceptible to brute force attacks due to PIN verification method.
  - Some devices do not fully disable WPS when selected, potentially leaving a security risk.

## Easy Connect (Device Provisioning Protocol - DPP)
- **Introduction**: Announced with WPA3 as a secure configuration method.
- **Mechanism**:
  - Uses public/private key pairs.
  - Communicates device public keys via QR codes or NFC tags.
- **Benefits**:
  - Fixes security issues associated with WPS.
  - Simplifies configuration, especially for IoT devices.

## Wi-Fi Protected Access 3 (WPA3)
- **Advancements**:
  - **Simultaneous Authentication of Equals (SAE)**: Enhances security during the authentication process.
  - **Enhanced Open**: Increases privacy on open networks without passwords.
  - **Updated Cryptographic Protocols**: Shifts from AES CCMP to AES GCMP, with stronger encryption for enterprise and personal use.
  - **Wi-Fi Easy Connect**: Facilitates secure device connections through QR code scanning.
- **Compatibility**:
  - Supports latest 802.11 standards (Wi-Fi 6/802.11ax, Wi-Fi 5/802.11ac, Wi-Fi 4/802.11n).
  - Requires devices to support WPA3 natively or through updates.

## Key Points
- Wireless networks must be configured with security settings to prevent unauthorized access.
- The evolution from WEP to WPA3 highlights significant improvements in Wi-Fi security standards.
- WPA3 introduces robust security features to mitigate vulnerabilities found in WPA2.
- Device support for the latest Wi-Fi standards and security specifications is crucial for maximizing network security and performance.
