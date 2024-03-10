---
tags: 
topic: sec_endpoints
subTopic: mobile_location
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_location
cert: Sec+
---
# Location Services
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Geolocation

- **Definition**: Use of network attributes to estimate the physical position of a device.
- **Systems Used**:
  - **GPS (Global Positioning System)**: Determines device's position via satellite information.
  - **IPS (Indoor Positioning System)**: Uses triangulation from radio sources like cell towers and Wi-Fi access points.

## Privacy Concerns

- Location services can track an individual's movements, posing privacy risks.
- Many apps require location access, potentially sharing and storing this data.
- Risks include stalking, social engineering, and identity theft if data is accessed by attackers.

## Geofencing and Camera/Microphone Enforcement

- **Geofencing**: Creating virtual boundaries for real-world geographic areas.
- **Uses**:
  - Controlling camera or video functions.
  - Context-aware authentication.
  - An organization may limit device functionality outside a defined perimeter.
- **Device Management Example**:
  - Using Microsoft Intune to restrict permissions like camera and screen capture.

## GPS Tagging

- **Definition**: Adding geographical identification metadata to media.
- **Concerns**:
  - Sensitive personal and organizational information.
  - GPS-tagged media on social media can reveal an individual's location and movements.
- **Example**:
  - A Russian soldier inadvertently disclosed troop positions via GPS-tagged selfies on Instagram.

# Cellular and GPS Connection Methods

## Cellular/Mobile Data Connections

- **Usage**: For data communication in smartphones, tablets, and laptops.
- **Security Concerns**: Mobile data connections can bypass enterprise network protections.
- **Protection Strategies**:
  - Implement controls on endpoints for security and privacy of corporate data.
  - Use technologies like VPNs, MDM, mobile threat defense, and DLP.

## Global Positioning System (GPS)

- **GPS Sensor**: Triangulates device position using signals from GPS satellites.
- **Assisted GPS (A-GPS)**:
  - Utilizes cellular data to obtain initial coordinates from the nearest cell tower.
  - Adjusts for the device's position relative to the tower for faster location fixing.
- **Satellite Systems**:
  - Operated by various entities including the US (GPS), EU (Galileo), Russia (GLONASS), and China (BeiDou).
- **Security Risks**:
  - GPS signals can be jammed or spoofed, potentially defeating mechanisms like geofencing.

## Device Management Example

- **Intune for Android Connectivity**:
  - Locking down Android connectivity, with many settings specific to Samsung KNOX-capable devices.
