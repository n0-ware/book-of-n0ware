---
tags:
topic: "sec_information"
subTopic: "logs"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_logs" 
cert: "Sec+"
---
# Host and OS Logs
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

Operating systems maintain logs to record events and interactions with the system. These logs serve various purposes and provide crucial information for system monitoring and troubleshooting. Here's an overview of key host operating system logs:

## Authentication Events

- **Purpose**: Record user login and logout attempts, as well as requests for special or administrative privileges.
- **Windows**: Found in the Security event log, includes both successful and failed authentication events.
- **Linux**: Authentication events are typically logged in files like /var/log/auth.log (Debian/Ubuntu) or /var/log/secure (RedHat/CentOS/Fedora).
- **macOS**: Authentication-related events can be accessed using macOS's unified logging system.

## File System Events

- **Purpose**: Record permissions-related events, such as access to files, read/write operations, and permission changes.
- **Configuration**: File system auditing needs to be explicitly configured to prevent generating excessive data.
- **Windows**: Recorded in the Security event log when auditing is enabled.
- **Linux**: File system events are typically logged in /var/log/messages or /var/log/syslog, and some are copied to individual log files.
- **macOS**: Access to files and system policy violations are logged using macOS's unified logging system.

## Windows Logs

- **Application**: Records events generated by application processes, including crashes and software installations.
- **Security**: Contains audit events such as login failures and denied access.
- **System**: Records events related to the operating system's kernel processes and services.

## Linux Logs

- **Variability**: Linux logging can vary by distribution, with some using syslog and others using Journald with a binary file format.
- **Key Log Files**: /var/log/messages or /var/log/syslog stores system-generated events, while authentication-related data is found in /var/log/auth.log (Debian/Ubuntu) or /var/log/secure (RedHat/CentOS/Fedora).
- **Package Manager Log**: Stores information about software installation and updates, depending on the package manager used (e.g., apt, yum, dnf).

## macOS Logs

- **Unified Logging System**: macOS uses a unified logging system that can be accessed through the Console app or the log command.
- **Security-Related Events**: Security-related events in macOS logs include login (com.apple.login), app installs (com.apple.install), and system policy violations (com.apple.syspolicy.exec).

Operating system logs are essential for monitoring, troubleshooting, and ensuring the security and integrity of the host system. They provide valuable insights into system behavior and events.