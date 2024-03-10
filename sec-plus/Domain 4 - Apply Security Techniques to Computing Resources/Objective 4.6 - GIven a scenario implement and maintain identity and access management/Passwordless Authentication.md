---
tags:
topic: "sec_iam"
subTopic: "authentication"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_authentication" 
cert: "Sec+"
---
# Passwordless Authentication
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`
## Overview
- **Definition**: Authentication method that eliminates knowledge-based factors, such as passwords, from the system.
- **Technology**: Utilizes FIDO2 with WebAuthn specifications for implementation.

## Authentication Process
1. **User Authentication Options**:
   - Roaming authenticator (e.g., security key).
   - Platform authenticator (e.g., Windows Hello, Face ID/Touch ID for macOS and iOS).
2. **Local Gesture Confirmation**:
   - Users confirm presence through a secure method like fingerprint, face recognition, or PIN.
   - Credential validation occurs locally by the authenticator.
3. **Registration with Relying Party**:
   - Authenticator generates a public/private key pair for each new relying party.
   - Public key is registered with the user's account on the web service.
4. **Authentication Challenge**:
   - User unlocks the private key with a local gesture.
   - Private key signs a confirmation, sent to the relying party for verification.
5. **Relying Party Verification**:
   - Uses the public key to verify the signature and authenticate the session.

## Benefits
- Provides security comparable to smart card authentication without needing digital certificates and PKI.
- Simplifies management and enhances user experience by eliminating passwords.

## FIDO2 WebAuthn Advancements
- Adds an API for web applications to authenticate users without passwords.
- Compatible with most FIDO U2F authenticators.

## Security Considerations
- **Authenticator Trust**: Must be resistant to spoofing or cloning.
- **Attestation Mechanism**:
  - Authenticators prove trustworthiness during registration.
  - Attestation keys identify brand and model, supporting cryptographic requirements without compromising privacy.
