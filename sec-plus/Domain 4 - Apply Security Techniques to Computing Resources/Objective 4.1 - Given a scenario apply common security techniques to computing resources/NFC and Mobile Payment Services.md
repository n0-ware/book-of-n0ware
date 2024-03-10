---
tags:
topic: "sec_mobile"
subTopic: "null"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_null" 
cert: "Sec+"
---
# NFC and Mobile Payment Services
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Near-Field Communication (NFC)

- **Technology**: Based on radio frequency ID (RFID), incorporated into smartphones for various uses.
- **Applications**:
  - Reading passive RFID tags.
  - Configuring connections (e.g., Bluetooth pairing).
  - Information exchange (e.g., contact cards).
- **Typical Use Case**: "Smart" posters for opening webpages via NFC tags.
- **Security Concerns**:
  - Vulnerable to attacks exploiting tag handling or directing devices to malicious webpages.
  - Lacks encryption, making eavesdropping and on-path attacks possible.

## Mobile Payment Services

- **Use of NFC**: For contactless payments via point-of-sale (PoS) machines.
- **Configuration**: Users enter credit card information into a mobile wallet app, which uses a one-time token for transactions.
- **Major Mobile Wallet Apps**:
  - Apple Pay.
  - Google Pay (formerly Android Pay).
  - Samsung Pay.

## Vulnerabilities

- **Eavesdropping**: Possible with certain antenna configurations, even from a distance.
- **Skimming**: Risk of information theft in crowded areas with a reader device.
- **Data Corruption**: Similar to a DoS attack, by flooding RF signals to interrupt data transfer.
- **Credit/Bank Card Skimming**:
  - Potential theft of card number and expiration date.
  - Direct fraudulent transactions via NFC are difficult due to the need for a valid merchant account and quick detection of fraud.
