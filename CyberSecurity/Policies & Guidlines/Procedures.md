Policies and guidelines set a framework for behavior. Procedures define step-by-step instructions and checklists for ensuring that a task is completed in a way that complies with policy.

### Personnel Management

Identity and access management (IAM) involves both IT/security procedures and technologies and Human Resources (HR) policies. Personnel management policies are applied in three phases:

- **Recruitment (hiring)**—locating and selecting people to work in particular job roles. Security issues here include screening candidates and performing background checks.
- **Operation (working)**—it is often the HR department that manages the communication of policy and training to employees (though there may be a separate training and personal development department within larger organizations). As such, it is critical that HR managers devise training programs that communicate the importance of security to employees.
- **Termination or Separation (firing or retiring)**—whether an employee leaves voluntarily or involuntarily, termination is a difficult process, with numerous security implications.

### Background Checks

A background check determines that a person is who they say they are and are not concealing criminal activity, bankruptcy, or connections that would make them unsuitable or risky. Employees working in high confidentiality environments or with access to high-value transactions will obviously need to be subjected to a greater degree of scrutiny. For some jobs, especially federal jobs requiring a security clearance, background checks are mandatory. Some background checks are performed internally, whereas others are done by an external third party.

### Onboarding

Onboarding at the HR level is the process of welcoming a new employee to the organization. The same sort of principle applies to taking on new suppliers or contractors. Some of the same checks and processes are used in creating customer and guest accounts.

As part of onboarding, the IT and HR function will combine to create an account for the user to access the computer system, assign the appropriate privileges, and ensure the account credentials are known only to the valid user. These functions must be integrated to avoid creating accidental configuration vulnerabilities, such as IT creating an account for an employee who is never actually hired. Some of the other tasks and processes involved in onboarding include the following:

- **Secure Transmission of Credentials**—creating and sending an initial password or issuing a smart card securely. The process needs protection against rogue administrative staff. Newly created accounts with simple or default passwords are an easily exploitable backdoor.
- **Asset Allocation**—provision computers or mobile devices for the user or agree to the use of bring-your-own-device handsets.
- **Training/Policies**—schedule appropriate security awareness and role-relevant training and certification.

IAM automation can streamline onboarding by automating the provisioning and access management tasks associated with new employees. It enables the automated creation and configuration of user accounts, assignment of appropriate access privileges based on established roles and access policies, and integration with HR systems for efficient new employee data synchronization. IAM automation reduces manual effort, ensures consistency, and improves security by enforcing standardized access controls, ultimately accelerating onboarding while maintaining strong security practices.

### Playbooks

Playbooks are essential to establishing and maintaining organizational procedures by establishing a central repository of well-defined, standardized strategies and tactics. They guide personnel to ensure consistency in operations and improve quality and effectiveness.

Playbooks facilitate knowledge sharing and continuity as employees move into new roles or leave the organization. Playbooks also mitigate risk by documenting critical procedures and preserving institutional knowledge. Playbooks help new team members quickly learn established processes while existing team members have a reference point for their tasks.

Moreover, playbooks act as a tool for quality assurance and continuous improvement. Clearly defining processes and the best practices to handle them makes it easier to identify and improve problem areas. By using playbooks, organizations can monitor the use and effectiveness of procedures over time and modify them as necessary to foster an environment of continual learning and development.

Most significantly, playbooks are essential in incident response and crisis management because they detail emergency procedures and contingency plans vital to steering activities during an emergency or crisis. Playbooks help incident response teams make quick decisions and work more effectively under stress, leading to more resilient operations and reducing the likelihood and impact of major security incidents.

Several best practice guides and frameworks are available to assist in developing playbooks, such as The MITRE ATT&CK framework [https://attack.mitre.org](https://attack.mitre.org/) and NIST Special Publication 800-61 [https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final).

### Change Management

The implementation of changes should be carefully planned, with consideration for how the change will affect dependent components. For most significant or major changes, organizations should attempt to trial the change first. Every change should be accompanied by a rollback (or remediation) plan, so that the change can be reversed if it has harmful or unforeseen consequences. Changes should also be scheduled sensitively if they are likely to cause system downtime or other negative impact on the workflow of the business units that depend on the IT system being modified. Most networks have a scheduled maintenance window period for authorized downtime. When the change has been implemented, its impact should be assessed and the process reviewed and documented to identify any outcomes that could help future change management projects.

### Offboarding

Offboarding ensures that an employee leaves a company gracefully, including an exit interview for feedback. Offboarding is also used when a project with contractors or third parties ends. In terms of security, there are several processes that must be completed:

- **Account Management**—disable the user account and privileges. Ensure that any information assets created or managed by the employee but owned by the company are accessible (in terms of encryption keys or password-protected files).
- **Company Assets**—retrieve mobile devices, keys, smart cards, USB media, and so on. The employee will need to confirm (and in some cases prove) that they have not retained copies of any information assets.
- **Personal Assets**—wipe employee-owned devices of corporate data and applications. The employee may also be allowed to retain some information assets (such as personal emails or contact information), depending on the policies in force.

The departure of some types of employees should trigger additional processes to re-secure network systems. Examples include employees with detailed knowledge of security systems and procedures, and access to shared or generic account credentials. These credentials must be changed immediately.