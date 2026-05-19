As well as events recorded by the operating system, hosts are also likely to generate application logs, including logs from host-based security software.

### Application Logs

An application log file is simply one that is managed by an application rather than the OS. The application may use Event Viewer or syslog to write event data using a standard format, or it might write log files to its own application directories in whatever format the developer has selected.

In Windows Event Viewer, there is a specific application log, which can be written to by any authenticated account. There are also separate custom application and service logs, which are managed by specific processes. The app developer chooses which log to use or whether to implement a logging system without using Event Viewer. Check the product documentation to find out where events for a particular software app are logged.

### Endpoint Logs

An endpoint log is likely to refer to events monitored by security software running on the host rather than by the OS itself. This can include host-based firewalls and intrusion detection, vulnerability scanners, and antivirus/antimalware protection suites. Suites that integrate these functions into a single product are often referred to as an endpoint protection platform (EPP), endpoint detection and response (EDR), or extended detection and response (XDR). These security tools can be directly integrated with a SIEM using agent-based software.

Summarizing events from endpoint protection logs can show overall threat levels, such as amount of malware detected, number of host intrusion detection events, and numbers of hosts with missing patches. Close analysis of detection events can assist with attributing intrusion events to a specific actor and developing threat intelligence of tactics, techniques, and procedures.

![A page titled, Event viewer.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/2238-1692974873354.png) Description

The lists of folders is on the left. The center section is divided into two parts. The top part is titled operational, number of events 162. The table lists the level, date and time, source, event ID, and task category. The bottom part is titled, event 1117, window defender. The general tab is selected. The information such as log name, source, event ID, level, user, opcode, more information, logged date and time, task category, keywords, and computer is listed below. The menu on the right is titled, actions.

Windows Defender logging detection and quarantine of malware to Event Viewer. (Screenshot used with permission from Microsoft.)

### Vulnerability Scans

While there is usually a summary report, a vulnerability scanner can be configured to log each vulnerability detected to a SIEM. Vulnerabilities can include missing patches and noncompliance with a baseline security configuration. The SIEM will be able to retrieve a list of these logs for each host. Depending on the date of the last scan, it may be difficult to identify from the log data which have been remediated, but in general terms, this will provide useful information about whether a host is properly configured.