When data has been collected and aggregated, the SIEM can be used to implement alerting, reporting, and archiving activities.

Note that these activities can be performed manually or automated using discrete tools for each security appliance. The advantage of a SIEM is to consolidate the activities to a single management interface. This consolidated functionality referred to as a "single pane of glass" refers to the enhanced visibility into a complex environment that such software offers.

### Alerting

A SIEM can then run correlation rules on indicators extracted from the data sources to detect events that should be investigated as potential incidents. An analyst can also filter or query the data based on the type of incident that has been reported.

Correlation means interpreting the relationship between individual data points to diagnose incidents of significance to the security team. A SIEM correlation rule is a statement that matches certain conditions. These rules use logical expressions, such as AND and OR, and operators, such as == (matches), < (less than), > (greater than), and in (contains). For example, a single-user login failure is not a condition that should raise an alert. Multiple user login failures for the same account, taking place within the space of one hour, is more likely to require investigation and is a candidate for detection by a correlation rule.

Error.LoginFailure > 3 AND LoginFailure.User AND Duration < 1 hour

As well as correlation between indicators observed in the collected data, a SIEM is likely to be configured with a threat intelligence feed. This means that data points observed in the collected network data can be associated with known threat actor indicators, such as IP addresses and domain names.

Each alert will be dealt with by the incident response processes of analysis, containment, eradication, and recovery. When used in conjunction with a SIEM, two particular steps in alert response and remediation deserve particular attention:

- Validation during the analysis process is how the analyst decides whether the alert is a true positive and needs to be treated as an incident. A false positive is where an alert is generated, but there is no actual threat activity.
- Quarantine is the step of isolating the source of indicators, such as a network address, host computer, or file.

Alert response and remediation steps will often be guided by a playbook that assists the analyst with applying all incident response processes for a given scenario. One of the advantages of SIEM and advanced security orchestration, automation, and reporting (SOAR) solutions is to fully or partially automate validation and remediation. For example, a quarantine action could be available as a mouse-click action via an integration with a firewall or endpoint protection product. Validation is made easier by being able to correlate event data to known threat data and pivot between sources, such as inspecting the packets that triggered a particular IDS alert.

### Reporting

Reporting is a managerial control that provides insight into the status of the security system. A SIEM can assist with reporting activity by exporting summary statistics and graphs. Report formats and contents are usually tailored to meet the needs of different audiences:

- Executive reports provide a high-level summary for decision-makers. This guides planning and investment activity.
- Manager reports provide cybersecurity and department leaders with detailed information. This guides day-to-day operational decision-making.
- Compliance reports provide whatever information is required by a regulator.

Determining which metrics are most useful in terms of reporting is always very challenging. The following types illustrate some common use cases for reporting:

- Authentication data, such as failed login attempts, and critical file audit data.
- Hosts with missing patches and/or configuration vulnerabilities.
- Privileged user account anomalies, such as out-of-hours use or excessive requests for elevated permissions.
- Incident case management statistics, such as overall volume, open cases, time to resolve, and so on.
- Trend reporting to show changes to key metrics over time.

### Archiving

A SIEM can enact a retention policy so that historical log and network traffic data is kept for a defined period. This allows for retrospective incident and threat hunting and can be a valuable source of forensic evidence. It can also meet compliance requirements to hold archives of security information. SIEM performance will degrade if an excessive amount of data is kept available for live analysis. A log rotation scheme can be configured to move outdated information to archive storage.