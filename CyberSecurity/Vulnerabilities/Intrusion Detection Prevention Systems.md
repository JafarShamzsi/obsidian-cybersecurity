Intrusion detection systems (IDS) and intrusion prevention systems (IPS) play critical roles in security operations. Both systems monitor network traffic, looking for suspicious patterns or activities that could indicate a network or system intrusion. However, they differ in their capabilities and responses to perceived threats.

Host-based and network-based intrusion detection systems (IDS) and intrusion prevention systems (IPS) each offer unique advantages in securing a network and using both in conjunction often leads to a more robust security posture. Host-based IDS/IPS (HIDS/HIPS) are installed on individual systems or servers, and they monitor and analyze system behavior and configurations for suspicious activities. HIDS/HIPS are particularly effective at identifying insider threats, detecting changes in system files, and monitoring non-network events like local logins and system processes. This makes them essential for protecting critical systems from internal and external threats.

OSSEC is an open-source HIDS solution that performs log analysis, integrity checking, Windows registry monitoring, rootkit detection, real-time alerting, and active response. It is compatible with multiple platforms, including Linux, Windows, and macOS.

Network-based IDS/IPS (NIDS/NIPS) monitor network traffic. They look for patterns or signatures of known threats and unusual network packet behavior. NIDS/NIPS are effective at identifying and responding to threats across multiple systems, like distributed denial-of-service (DDoS) attacks or network scanning activities.

Despite their strengths, neither type can wholly substitute for the other. HIDS/HIPS are confined to the activities on the host on which they are installed, so they do not effectively detect network-wide anomalies. Similarly, NIDS/NIPS can't provide detailed visibility into host-specific activities or detect threats that don't involve network traffic.

### Examples of IDS and IPS Tools

Intrusion detection systems (IDS), such as Snort, are designed to detect potential threats and generate alerts. IDS systems are passive, inspecting network traffic, identifying potential threats based on predefined rules or unusual behavior, and sending alerts to administrators. They do not actively block or prevent threats but notify of the potential issue. This allows security analysts to investigate the alert, avoiding disruptions to network traffic or potentially blocking legitimate traffic caused by false positives.

An excellent description and breakdown of Snort rules is available at [https://snort.org/documents#OfficialDocumentation](https://snort.org/documents/snort-rule-infographic).

In contrast, intrusion prevention systems (IPS), like Suricata, are proactive security tools that detect potential threats and take action to prevent or mitigate them. An IPS identifies a threat using methods similar to an IDS and can block traffic from the offending source, drop malicious packets, or reset connections to disrupt an attack. While this can immediately prevent damage, there is a risk of false positives leading to blocking legitimate traffic.

Important IDS & IPS tools include the following:

- **Snort** is one of the most well-known IDS/IPS tools. It uses a rule-driven language, which combines the benefits of signature, protocol, and anomaly-based inspection methods, providing robust detection capabilities. Snort's open-source nature and widespread adoption have led to a large community contributing rules and configurations, making it a versatile tool for various environments.
- **Suricata** is a high-performance open source IDS/IPS/NSM engine. Suricata is designed to take full advantage of modern hardware and deliver higher performance and scalability than Snort. Suricata can function as an IDS or an IPS, and is compatible with Snort rulesets, making it a highly flexible option for network security.
- **Security Onion** is a Linux distribution designed for intrusion detection, network security monitoring, and log management. It includes both Snort and Suricata, along with a host of other tools, to provide a complete platform for network security. This integration provides a holistic view of network activity, enabling administrators to correlate data from different tools and obtain a comprehensive understanding of the network's security posture.

![A Screengrab of Security Onion Alerts dashboard.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/4653-1692974870238.png) Description

Alerts option is selected from the left pane. The right pane titled Alerts (Total found: 102) shows the search bar with the dropdown that reads, Group by name, Module. Another dropdown on the right allows the users to choose the timespan. Fetch limit is set to 50. The filter results are displayed in the form of a table that lists the count, rule dot name, event dot module, and event dot security underscore label.

The Security Onion Alerts dashboard displaying several alerts captured using the Emerging Threats (ET) ruleset and Suricata. (Screenshot used with permission from Security Onion.)