Dashboards and reports also assist with real-time monitoring of host system and application/service status.

### System Monitors and Logs

A system monitor implements the same functionality as a network monitor for a computer host. Like switches and routers, server hosts can report health status using SNMP traps.

Logs are one of the most valuable sources of security information. A system log can be used to diagnose availability issues. A security log can record both authorized and unauthorized uses of a resource or privilege. Logs function both as an audit trail of actions and (if monitored regularly) provide a warning of intrusion attempts. Log review is a critical part of security assurance. Only referring to the logs following a major incident is missing the opportunity to identify threats and vulnerabilities early and to respond proactively.

Logs typically associate an action with a particular user. This is one of the reasons why it is critical that users not share login details. If a user account is compromised, there is no means of tying events in the log to the actual attacker.

### Application and Cloud Monitors

SNMP offers fairly limited functionality. There are numerous proprietary monitoring solutions for infrastructure, application, database, and cloud environments. Some are designed for on-premises and some for cloud, while some support hybrid monitoring of both types of environment. An application monitor will include a basic heartbeat test to verify that it is responding. Other factors to monitor include number of sessions and requests, bandwidth consumption, CPU and memory utilization, and error or security alert conditions. Cloud monitors will assess different facets of cloud services, such as network bandwidth, virtual machine status, and application health.

### Vulnerability Scanners

A vulnerability scanner will report the total number of unmitigated vulnerabilities for each host. Consolidating these results can show the status of hosts across the whole network and highlight issues with a particular patch or configuration issue.

### Antivirus

Most hosts should be running some type of antivirus scan (A-V) software. While the A-V monitor remains popular, these suites are better conceived of as endpoint protection platforms (EPPs) or next-gen A-V. These detect malware by signature regardless of type, though detection rates can vary quite widely from product to product. Many suites also integrate with user and entity behavior analytics (UEBA) and use AI-backed analysis to detect threat actor behavior that has bypassed malware signature matching.

Antivirus will usually be configured to block a detected threat automatically. The software can be configured to generate a dashboard alert or log via integration with a SIEM.

### Data Loss Prevention

Data loss prevention (DLP) mediates the copying of tagged data to restrict it to authorized media and services. As with antivirus scanning, monitoring statistics for DLP policy violations can show whether there are issues, especially where the results show trends over time.