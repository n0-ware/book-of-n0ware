---
tags:
topic: "sec_monitoring"
subTopic: "alerting"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_alerting" 
cert: "Sec+"
---
# Alerting and Monitoring Activities
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Security Information and Event Management (SIEM) systems play a pivotal role in cybersecurity by consolidating alerting, reporting, and archiving activities into a single management interface, often referred to as a "single pane of glass." This enhanced visibility is crucial for monitoring complex environments effectively.

## Alerting

- **Correlation Rules**: SIEM uses logical expressions to detect significant security events from the aggregated data, such as multiple login failures within a short timeframe.
- **Threat Intelligence Integration**: Enhances detection capabilities by associating observed data with known threat actor indicators.
- **Response and Remediation**: Involves validation to determine true positives and quarantine measures to isolate threats. Advanced SIEM and SOAR solutions may automate these steps.

## Reporting

- **Purpose**: Provides insights into the security system's status, supporting decision-making at various organizational levels.
- **Types of Reports**:
  - **Executive Reports**: High-level summaries for strategic planning.
  - **Manager Reports**: Detailed operational information for day-to-day management.
  - **Compliance Reports**: Information required by regulators.

- **Use Cases for Reporting**:
  - Authentication and critical file audit data.
  - Hosts with vulnerabilities due to missing patches or configurations.
  - Anomalies in privileged user accounts.
  - Incident management statistics.
  - Trend reporting for key metrics over time.

## Archiving

- **Retention Policy**: Defines the period for keeping historical log and network traffic data, supporting retrospective analyses and compliance.
- **Log Rotation Scheme**: Manages data to prevent performance degradation by moving older information to archive storage.

SIEM systems are essential for an organization's cybersecurity infrastructure, offering sophisticated tools for monitoring, alerting, and managing security threats and vulnerabilities.
# Alert Tuning in SIEM Systems

Alert tuning is a crucial process in Security Information and Event Management (SIEM) systems, aimed at optimizing the balance between identifying legitimate threats and minimizing false positives.

## Key Concepts

### Criticality Levels

- **Log Only**: Event is recorded in the SIEM database without active notification.
- **Alert**: Event appears on a dashboard for analyst review, leading to validation or dismissal.
- **Alarm**: Automatically classified as critical, triggering immediate notification to incident handlers.

### False Positives and Alert Fatigue

- **Issue**: Excessive false positives lead to alert fatigue, risking oversight of critical alerts.
- **Challenge**: Balancing sensitivity to reduce false positives without increasing the risk of false negatives.

### False Negatives

- A significant security weakness where malicious activity is not detected or alerted.
- Threat hunting activities often aim to identify and mitigate false negatives.

### True Negatives

- Events correctly identified as non-threatening, important for assessing system performance.

## Alert Tuning Techniques

### Refining Detection Rules

- Adjust rule parameters or mute certain alerts to reduce dashboard clutter.
- Configure rules to aggregate notifications to manage frequent triggers more efficiently.

### Managing Alert "Floods"

- Redirect excessive alerts caused by network changes or misconfigurations to specialized teams or agents.

### Infrastructure-Related Alerts

- Assign alerts related to misconfigurations to dedicated infrastructure teams, separating them from incident response tasks.

### Continuous Monitoring and Feedback

- Utilize managerial oversight and analyst feedback to adjust alert sensitivity and rule parameters.
- Leverage experience to automate rule processing with Security Orchestration, Automation, and Response (SOAR) solutions.

### Machine Learning Analysis

- Employ ML to analyze alert patterns and responses, aiming to auto-tune rules to reduce false negatives and maintain true positives.

Effective alert tuning requires a dynamic approach, leveraging both technology and human insight to maintain an optimal balance between alert sensitivity and specificity. This ensures that SIEM systems remain effective tools in the identification and mitigation of cybersecurity threats.
