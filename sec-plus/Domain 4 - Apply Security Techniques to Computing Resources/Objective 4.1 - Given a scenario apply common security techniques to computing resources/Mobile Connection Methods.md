---
tags: 
topic: sec_mobile
subTopic: wifi
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_wifi
cert: Sec+
---
# Mobile Connection Methods
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Wi-Fi Connections

- **Security with WPA3**: Strong security on corporate networks reduces risk of eavesdropping and attacks.
- **Risks**:
  - Connecting to open or rogue access points increases risks of attacks and session compromise.
  - DNS spoofing attacks can compromise secure sessions.

## Personal Area Networks (PANs)

- **Purpose**: Enables connectivity between a mobile device and peripherals.
- **Security**: Peer-to-peer functions should generally be disabled to prevent corporate network breaches.

## Ad Hoc Wi-Fi and Wi-Fi Direct

- **Ad Hoc Networks**: Peer-to-peer connections without permanent access points. No standard support.
  - MITRE project for Android ad hoc networking (SMART or SPAN).
- **Wi-Fi Direct**:
  - One-to-one connections, with one device acting as a soft access point.
  - Uses Wi-Fi Protected Setup (WPS), which is vulnerable.
  - Android supports Wi-Fi Direct AP; iOS uses proprietary framework but can connect to Wi-Fi Direct SoftAPs.

## Wireless Mesh Networks

- **Products**: From vendors like Netgear and Google, allowing peer-to-peer networking.
- **Interoperability**: Support for EasyMesh standard is increasing among products.

## Tethering and Hotspots

- **Functionality**:
  - Sharing a smartphone's Internet connection with other devices.
  - Can be over Wi-Fi (hotspot) or via USB/Bluetooth (tethering).
- **Enterprise Network Concerns**:
  - Typically disabled to prevent circumvention of security mechanisms like DLP or web filtering.
