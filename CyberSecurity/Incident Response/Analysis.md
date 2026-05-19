After the detection process reports one or more indicators, in the analysis process, the first responder investigates the data to determine whether a genuine incident has been identified and what level of priority it should be assigned. Conversely, the report might be categorized as a false positive and dismissed. Classification of a true positive incident event often relies on correlating multiple indicators. For a complex or high-impact event, the analysis might be escalated to senior CIRT team members.

When an incident is verified as a true positive, the next objective is to identify the type of incident and the data or resources affected. This establishes incident category and impact and allows the assignment of a priority level.

### Impact

Several factors affect the process of determining impact:

- **Data integrity**—the most important factor in prioritizing incidents will often be the value of data that is at risk.
- **Downtime**—is the degree to which an incident disrupts business processes, another very important factor. An incident can either degrade (reduce performance) or interrupt (completely stop) the availability of an asset, system, or business process.
- **Economic/publicity**—both data integrity and downtime have important economic effects in the short term and the long term. Short-term costs involve incident response and lost business opportunities. Long-term economic costs may involve damage to reputation and market standing.
- **Scope**—(broadly the number of systems affected) is not a direct indicator of priority. A large number of systems might be infected with a type of malware that degrades performance but is not a data breach risk. This might even be a masking attack as the adversary seeks to compromise data on a single database server storing top-secret information.
- **Detection time**—research has shown that more than half of data breaches are not detected for weeks or months after the intrusion occurs, while in a successful intrusion, data is typically breached within minutes. Systems used to search for intrusions must be thorough and the response to detection must be fast.
- **Recovery time**—some incidents require lengthy remediation as the system changes required are complex to implement. This extended recovery period should trigger heightened alertness for continued or new attacks.

### Category

Incident categories and definitions ensure that all response team members and other organizational personnel have a shared understanding of the meaning of terms, concepts, and descriptions.

Effective incident analysis depends on threat intelligence. This research provides insight into adversary tactics, techniques, and procedures (TTPs). Insights from threat research can be used to develop specific tools and playbooks to deal with event scenarios. A key tool for threat research is the framework used to describe the stages of an attack. These stages are often referred to as a cyber kill chain , following the influential white paper Intelligence-Driven Computer Network Defense commissioned by Lockheed Martin ([lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf](https://wmx-api-production.s3.amazonaws.com/courses/54312/supplementary/LM-White-Paper-Intel-Driven-Defense.pdf#)).

Description

Stages in the kill chain.

### Playbooks

The CIRT should develop profiles or scenarios of typical incidents, such as DDoS attacks, virus/worm outbreaks , data exfiltration by an external adversary, data modification by an internal adversary, and so on. This guides investigators in determining priorities and remediation plans.

A playbook is a data-driven standard operating procedure (SOP) to assist analysts in detecting and responding to specific cyber threat scenarios. The playbook starts with a report from an alert dashboard. It then leads the analyst through the analysis, containment, eradication, recovery, and lessons learned steps to take.