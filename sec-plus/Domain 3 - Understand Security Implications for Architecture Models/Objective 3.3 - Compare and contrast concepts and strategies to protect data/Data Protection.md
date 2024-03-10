---
tags: 
topic: sec_data
subTopic: data_protection
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_data_protection
cert: Sec+
---
	# sec_data
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

# Data Protection

Data protection strategies are tailored according to the state of the data: at rest, in motion, and in use.

## Data States

- **Data at Rest**: Persistent storage. Encrypt data and use Access Control Lists (ACLs) for authorized access.
- **Data in Transit (Motion)**: Data transmitted over networks. Protect with transport encryption protocols like TLS or IPSec.
- **Data in Use (Processing)**: Data in volatile memory (RAM, CPU cache). Use Trusted Execution Environment (TEE) for encryption in memory.

## Data Protection Methods

### Geographic Restrictions
Limit data access based on geographic locations to comply with data protection laws.

### Encryption
Convert data into a coded format accessible only with a key or password.

### Hashing
Convert data into a fixed-length string to verify integrity and securely store passwords.

### Masking
Replace sensitive data with fictional values while preserving format, commonly used in form password fields.

### Tokenization
Replace sensitive data with a token, used in payment processing to secure card information.

### Obfuscation
Modify data to prevent understanding or reverse engineering, used in software development to protect code.

### Segmentation
Divide networks and data into isolated components, limiting breach impact and improving security.

### Permission Restrictions
Control data access based on user permissions to ensure only authorized access.

Implementing these data protection methods based on the specific state and requirements of the data helps maintain confidentiality, integrity, and availability while complying with legal and regulatory standards.
