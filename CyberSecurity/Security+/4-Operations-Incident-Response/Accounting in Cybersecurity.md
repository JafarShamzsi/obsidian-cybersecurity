## Overview  
**Accounting**, also known as **auditing or logging**, ensures that all actions performed by subjects (users, devices, or processes) on objects (systems, files, or applications) are **tracked, recorded, and analyzed**. This helps in monitoring security events, detecting unauthorized activities, and maintaining compliance with industry regulations.

## Key Functions of Accounting  
- **Logging Events:**  
  - Records every access attempt, system change, or transaction.  
  - Example: A log entry records that *User123* accessed *SensitiveFile.doc* at *10:05 AM*.

- **Monitoring and Reviewing Logs:**  
  - Security teams analyze logs to detect suspicious activities.  
  - Example: An admin detects multiple failed login attempts from an unknown IP address.

- **Generating Audit Trails:**  
  - Provides a sequence of logged activities for investigations.  
  - Example: Tracing an attacker’s movements through system logs.

- **Detecting and Responding to Incidents:**  
  - Alerts are triggered when unauthorized access or anomalies are detected.  
  - Example: A security system flags a login from an unusual geographic location.

- **Compliance and Legal Requirements:**  
  - Organizations must retain logs for regulatory standards like **HIPAA, GDPR, PCI-DSS, and SOX**.  
  - Example: A financial institution logs transactions for **Sarbanes-Oxley (SOX)** compliance.

## Example Scenario: Accounting in Action  
**Scenario: Employee Access to a Database**  
1. **Identification** → Employee logs in using their credentials.  
2. **Authentication** → They provide a password and pass MFA.  
3. **Authorization** → They have permission to view records but not modify them.  
4. **Accounting** →  
   - The system logs all database queries performed by the employee.  
   - Unauthorized access attempts are flagged.  
   - Security analysts review the logs for investigation.

## Types of Logs Used in Accounting  
| **Log Type** | **Purpose** |
|-------------|------------|
| **Authentication Logs** | Track login attempts (success/failure). |
| **Access Logs** | Record which users accessed what resources. |
| **System Logs** | Capture OS-level events (startup, shutdown, errors). |
| **Application Logs** | Monitor user activity within software applications. |
| **Network Logs** | Track network traffic, firewall events, and VPN usage. |
| **Security Logs** | Log alerts related to security incidents. |

## Exam Tips  
- **Accounting ensures actions are logged and can be reviewed later.**  
- **It is part of the AAA (Authentication, Authorization, and Accounting) model.**  
- **Common tools include SIEM (Security Information and Event Management) solutions.**  
- **Logs should be protected to prevent tampering or deletion.**  
- **Accounting is crucial for forensic investigations and compliance.**  

## Related Topics  
- [[4-Operations-Incident-Response/Security Information and Event Management (SIEM)]]  
- [[3-Implementation/Authentication Methods]]  
- [[5-Governance-Risk-Compliance/Compliance and Legal Requirements]]  
- [[Glossary#AAA Model]]  

## Practice Questions  
1. **Which of the following best describes the purpose of accounting in cybersecurity?**  
   - A. Preventing unauthorized access to a system  
   - B. Verifying a user's identity before granting access  
   - C. Tracking and logging user activities for security and compliance  
   - D. Encrypting sensitive data stored in a database  
   - **Answer:** C. Tracking and logging user activities for security and compliance.  

2. **Which tool is commonly used for security event logging and analysis?**  
   - A. SIEM  
   - B. IDS  
   - C. IPS  
   - D. VPN  
   - **Answer:** A. SIEM (Security Information and Event Management).  

3. **Which of the following logs would record failed login attempts?**  
   - A. System logs  
   - B. Authentication logs  
   - C. Application logs  
   - D. Network logs  
   - **Answer:** B. Authentication logs.  

## Glossary Entries  
Copy and paste these into your `Glossary.md` file:  

### **Accounting (Cybersecurity)**  
The process of logging and monitoring user actions on a system to ensure security, compliance, and forensic analysis. It is a core component of the AAA (Authentication, Authorization, and Accounting) framework.

### **Audit Trail**  
A chronological record of system activities used for investigation and compliance. Helps trace unauthorized or malicious activities.

### **Security Information and Event Management (SIEM)**  
A security solution that aggregates, analyzes, and monitors logs from various sources to detect threats and generate alerts.

---
