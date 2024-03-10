---
tags:
topic: "sec_general"
subTopic: "crypto_tools"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_crypto_tools" 
cert: "Sec+"
---
# Cryptoprocessors and Secure Enclaves
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# Key Generation and Storage in Cryptography

## Key Generation Challenges
- **Randomness Requirement**: Cryptographic keys need high entropy for security.
- **Computer Limitations**: General computer hardware and software have low entropy.
- **PRNG and TRNG**: Pseudo RNG software approximates disorder, but true RNG hardware is superior.

## Key Storage Vulnerabilities
- **File System Storage**: Keys stored as regular files are susceptible to compromise.
- **Security Measures**: Ideal cryptographic storage should be tamper-evident for quick response to compromises.
- **GPG Key Generation**: Uses pseudo RNG, gains entropy from user interactions.

## Cryptoprocessor Utilization
- **Advantages**:
  - Dedicated to single function, reducing attack surface.
  - Performs operations like decryption and signing internally.
  - Prevents key material from leaving the processor.
- **Types**:
  - ***Trusted Platform Module (TPM)***: Integrated in CPU, versions 1.2 and 2.0 available. Version 2.0 is not backward compatible. 
	  - Specification for secure hardware-based storage of encryption keys, hashed passwords, and other user- and platform-identification information.
  - ***Hardware Security Module (HSM)***: Removable or dedicated hardware, including rack-mounted appliances, PCIe cards, and USB keys.
	  - An appliance for generating and storing cryptographic keys. This sort of solution may be less susceptible to tampering and insider threats than software-based storage.

## Hardware Security Module (HSM) Details
- **Form Factors**: Rack-mounted, plug-in, USB-connected, or virtual appliances.
- **Certification**: Vendors can certify HSMs against FIPS 140-2 standard.

## Cryptoprocessor and API Interaction
- **API Use**: Cryptoprocessors interact with applications via APIs like PKCS#11.
	- The Public-Key Cryptography Standards (PKCS) comprise a group of cryptographic standards that provide guidelines and application programming interfaces (APIs) for the usage of cryptographic methods. As the name PKCS suggests, these standards put an emphasis on the usage of public key (that is, asymmetric) cryptography.
**PKCS #11** is a cryptographic token interface standard, which specifies an API, called Cryptoki.
- **Accessibility**: Ensures keys are not directly accessible via the file system.

## Security Vulnerabilities and Mitigations
- **Decrypted Data in RAM**: Potential for malicious access.
- **Secure Enclave Implementation**:
	- CPU extensions that protect data stored in system memory so that an untrusted process cannot read it.
	- **Purpose**: Protects data in system memory from unauthorized processes, even root or system processes, unless authorized.
	- **Example**: Intel Software Guard Extensions (TEE secure enclave).
	- **Functionality**: Locks enclave to authorized, digitally signed processes only.
