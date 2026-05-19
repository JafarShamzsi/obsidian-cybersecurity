Three technologies have emerged as essential for verifying the authenticity of emails and preventing phishing and spam: Sender Policy Framework (SPF), Domain Keys Identified Mail (DKIM), and Domain-based Message Authentication, Reporting & Conformance (DMARC).

Sender Policy Framework (SPF) is an email authentication method that helps detect and prevent sender address forgery commonly used in phishing and spam emails. SPF works by verifying the sender's IP address against a list of authorized sending IP addresses published in the DNS TXT records of the email sender's domain. When an email is received, the receiving mail server checks the SPF record of the sender's domain to verify the email originated from one of the pre-authorized systems.

![A Screengrab displays the T X T records for Microsoft.com. One of the entries under the answer section is highlighted.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/9534-1692974871460.png)

Displaying the TXT records for microsoft.com using the dig tool. (Screenshot used with permission from Microsoft.)

DomainKeys Identified Mail (DKIM) leverages encryption features to enable email verification by allowing the sender to sign emails using a digital signature. The receiving email server uses a DKIM record in the sender's DNS record to verify the signature and the email's integrity.

Domain-based Message Authentication, Reporting & Conformance (DMARC) uses the results of SPF and DKIM checks to define rules for handling messages, such as moving messages to quarantine or spam, rejecting them outright, or tagging the message. DMARC also provides reporting capabilities, giving the owner of a domain visibility into which systems are sending emails on their behalf, including unauthorized activity.

![A Screengrab of DNS Checker.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/1280-1692974871651.png)

Performing a DMARC lookup using the DNSChecker website [https://dnschecker.org](https://dnschecker.org).

The combined use of SPF, DKIM, and DMARC significantly enhances email security by making it much more difficult for attackers to impersonate trusted domains, which is one of the most common tactics used in phishing and spam attacks. These protocols are essential tools in the fight against email-based threats because they provide essential mechanisms that help verify the authenticity of emails, maintain the integrity of the email content, and ensure the safe delivery of electronic communication.

### Email Gateway

An email gateway is the control point for all incoming and outgoing email traffic. It acts as a gatekeeper, scrutinizing all emails to remove potential threats before they reach inboxes. Email gateways utilize several security measures, including anti-spam filters, antivirus scanners, and sophisticated threat detection algorithms to identify phishing attempts, malicious URLs, and harmful attachments. Email gateways leverage DMARC, SPF, and DKIM to automate the authentication and validation of email senders, reducing the chances that spoofed or impersonated emails will be delivered.

Email gateways also play a critical role in policy enforcement by allowing organizations to create rules related to email content and attachments based on established policies or regulatory compliance requirements. Attachment blocking, content filtering, and data loss prevention are common tasks email gateways handle.

### Secure/Multipurpose Internet Mail Extensions

Secure/Multipurpose Internet Mail Extensions (S/MIME) is a protocol for securing email communications. It encrypts emails and enables sender authentication to ensure the confidentiality and integrity of email communications. S/MIME uses public key encryption techniques to secure email content (the "body" of email). S/MIME also incorporates digital signatures to support sender verification and ensure messages are unmodified. By providing encryption and authentication capabilities, S/MIME significantly enhances the security of email communication, but its implementation is often complicated and prone to misconfiguration.