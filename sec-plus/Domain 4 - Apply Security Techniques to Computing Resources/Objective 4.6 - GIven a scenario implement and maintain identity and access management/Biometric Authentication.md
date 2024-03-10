---
tags:
topic: "sec_iam"
subTopic: "biometrics"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_biometrics" 
cert: "Sec+"
---
# Biometric Authentication
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Biometric authentication is a security process that uses unique biological characteristics of individuals to verify identity. It offers a higher level of security compared to traditional passwords or PINs by utilizing something the user is. Here's a breakdown of how it works, its challenges, and its metrics for evaluation.

## Enrollment Process

1. **Biometric Sample Acquisition**: A sensor module captures the biometric sample (e.g., fingerprint, facial scan) from the user.
2. **Template Creation**: A feature extraction module processes the sample to create a unique mathematical template representing the user's biometric data.
3. **Verification**: When accessing a resource, the user's biometric data is re-scanned and compared to the stored template. Access is granted if the new scan matches the template within a certain tolerance level.

## Evaluation Metrics and Challenges

### False Rejection Rate (FRR)

- Represents instances where a legitimate user's biometric is incorrectly rejected.
- Also known as Type I error or false non-match rate (FNMR).

### False Acceptance Rate (FAR)

- Occurs when an unauthorized user is incorrectly authenticated.
- Also known as Type II error or false match rate (FMR).

### Crossover Error Rate (CER)

- The point where FRR and FAR are equal. A lower CER indicates a more reliable system.

### Throughput

- Measures the time required for template creation and authentication. Crucial for high-traffic environments.

### Failure to Enroll Rate (FER)

- Incidences where a user's biometric cannot be accurately captured or matched during enrollment.

## Common Biometric Methods

### Fingerprint Recognition

- Widely used due to its cost-effectiveness and straightforward process.
- Utilizes capacitive or optical sensors to detect unique ridge patterns.
- Susceptible to issues with moisture or dirt on the sensor.

### Facial Recognition

- Identifies users based on facial features (e.g., distance between eyes, nose shape).
- Employs optical and infrared sensors to enhance security and prevent spoofing.

## Challenges and Considerations

- **Privacy Concerns**: Users may find biometric data collection intrusive.
- **Accessibility**: The technology can be discriminatory or inaccessible for individuals with disabilities.
- **Cost and Implementation**: Some biometric scanners are expensive or challenging to integrate with mobile devices.
- **Environmental Sensitivity**: Performance can be affected by physical conditions (e.g., lighting for facial recognition, cleanliness for fingerprint sensors).

Biometric authentication combines advanced technology with unique personal attributes to provide secure and convenient access control. However, successful implementation requires careful consideration of its challenges, including privacy concerns, cost, and the potential for error rates, ensuring it complements an organization's overall security strategy.
