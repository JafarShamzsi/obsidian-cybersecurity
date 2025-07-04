Software designed to assist with managing security data inputs and provide reporting and alerting is often described as security information and event management (SIEM). The core function of a SIEM tool is to collect and correlate data from network sensors and appliance/host/application logs. In addition to logs from Windows and Linux-based hosts, this could include switches, routers, firewalls, IDS sensors, packet sniffers, vulnerability scanners, malware scanners, and data loss prevention (DLP) systems.

![](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/4116-1692974873870.png)

Wazuh SIEM dashboard—Configurable dashboards provide the high-level status view of network security metrics. (Screenshot used with permission from Wazuh Inc.)

### Agent-Based and Agentless Collection

Collection is the means by which the SIEM ingests security event data from various sources. There are three main types of security data collection:

- **Agent-based**—this approach means installing an agent service on each host. As events occur on the host, logging data is filtered, aggregated, and normalized at the host, then sent to the SIEM server for analysis and storage. Collection from Windows/Linux/macOS computers will tend to use agent-based collection. The agent must run as a process and could use from 50–500 MB of RAM, depending on the amount of activity and processing it does.
- Listener/collector—rather than installing an agent, hosts can be configured to push log changes to the SIEM server. A process runs on the management server to parse and normalize each log/monitoring source. This method is often used to collect logs from switches, routers, and firewalls, as these are unlikely to support agents. Some variant of the Syslog protocol is typically used to forward logs from the appliance to the SIEM.
- **Sensor**—as well as log data, the SIEM might collect packet captures and traffic flow data from sniffers. A sniffer can record network data using either the mirror port functionality of a switch or using some type of tap on the network media.

![](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/8597-1692974873920.png)

Agent configuration file for event sources to report to the Wazuh SIEM.

### Log Aggregation

As distinct from collection, **log aggregation** refers to normalizing data from different sources so that it is consistent and searchable. SIEM software features connectors or plug-ins to interpret (or parse) data from distinct types of systems and to account for differences between vendor implementations. Each agent, collector, or sensor data source will require its own parser to identify attributes and content that can be mapped to standard fields in the SIEM's reporting and analysis tools. Another important function is to normalize date/time zone differences to a single timeline.