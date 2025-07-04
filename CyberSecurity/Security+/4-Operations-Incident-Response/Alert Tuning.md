Correlation rules are likely to assign a criticality level to each match. Examples include the following:

- **Log only**—an event is produced and added to the SIEM's database, but it is not automatically classified.
- **Alert**—the event is listed on a dashboard or incident handling system for an agent to assess. The agent analyzes the event data and either dismisses it to the log or validates it and starts an incident case.
- **Alarm**—the event is automatically classified as critical, and a priority alarm is raised. This might mean emailing an incident handler or sending a text message.

Alert tuning is necessary to reduce the incidence of false positives. False positive alerts and alarms waste analysts' time and reduce productivity. Alert fatigue refers to the sort of situation where analysts are so consumed with dismissing numerous low-priority alerts that they miss a single high-impact alert that could have prevented a data breach. Analysts can become more preoccupied with looking for a quick reason to dismiss an alert than with properly evaluating the alert. Reducing false positives is difficult, however: firstly because there isn't a simple dial to turn for overall sensitivity, and secondly because reducing the number of rules that produce alerts increases the risk of false negatives.

A false negative is where the system fails to generate an alert about malicious indicators that are present in the data source. False negatives are a serious weakness in the security system. One of the purposes of threat hunting activity is to identify whether the monitoring system is subject to false negatives.

There is also a concept of true negatives. This is a measure of events that the system has properly allowed. Metrics for false and true negatives can be used to assess the performance of the alerting system.

Some of the techniques used to manage alert tuning include the following:

- Refining detection rules and muting alert levels—If a certain rule is generating multiple dashboard notifications, the parameters of the rule can be adjusted to reduce this, perhaps by adding more correlation factors. Alternatively, the alert can be muted to log-only status or configured so that it only produces a single notification for every 10 or 100 events.
- Redirecting sudden alert "floods" to a dedicated group—Changes in the network can cause a rule to start producing far more alerts than it should. Once it's confirmed that this is a false positive, rather than "spamming" each analyst's dashboard, it can be assigned to a dedicated agent or team to remediate.
- Redirecting infrastructure-related alerts to a dedicated group—Misconfigurations, such as deviance from a baseline, can cause continually high alert volumes. While these are important to fix, that is not the job of the incident response team and is better managed by an infrastructure team.
- Continuous monitoring of alert volume and analyst feedback—Managers should keep oversight of the system and be aware of risks from alert fatigue. The experience of individual analysts can be utilized to reduce alert sensitivity or change the parameters of a given rule or to automate processing of the rule using a SOAR solution.
- Deploying machine learning (ML) analysis—ML is able to rapidly analyze the sort of data sets produced by SIEM. It can be used to monitor how analysts are responding to alerts, and attempt to automatically tune the ruleset in a way that reduces false negatives without impacting true positives