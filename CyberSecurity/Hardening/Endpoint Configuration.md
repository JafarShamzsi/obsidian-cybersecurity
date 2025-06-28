If endpoint security is breached, there are several classes of vectors to consider for mitigation:

- **Social Engineering**—if the malware was executed by a user, use security education and awareness to reduce the risk of future attacks succeeding. Review permissions to see if the account could be operated with a lower privilege level.
- **Vulnerabilities**—if the malware exploited a software fault, install the patch or isolate the system until a patch can be developed.
- **Lack of Security Controls**—if the attack could have been prevented by endpoint protection/A-V, host firewall, content filtering, DLP, or MDM, investigate the possibility of deploying them to the endpoint. If this is not practical, isolate the system from being exploited by the same vector.
- **Configuration Drift**—if the malware exploited an undocumented configuration change (shadow IT software or an unauthorized service/port, for instance), reapply the baseline configuration and investigate configuration management procedures to prevent this type of ad hoc change.
- **Weak Configuration**—if the configuration was correctly applied, but was exploited anyway, review the template to devise more secure settings. Make sure the template is applied to similar hosts.

### Access Control

Access control refers to regulating and managing the permissions granted to individuals, software, systems, and networks to access resources or information. Access controls ensure that only authorized entities can perform specific actions or access certain data, while unauthorized entities are denied access. Access control concepts apply to networks, physical access, data, applications, and the cloud.

### Principle of Least Privilege

Implementing the principle of least privilege (PoLP) is a cornerstone of improving endpoint protection and minimizing the risk of security issues. The principle of least privilege dictates that users, applications, and processes should only be granted the minimum permissions necessary to complete their duties and nothing more.

There are several practical methods for implementing least privilege. An essential first step to effectively implementing least privilege is thoroughly auditing user roles, privileges, and responsibilities. This process allows organizations to understand what access each user needs to perform their job role effectively. Access controls and permissions can be adjusted to adopt a principle of least privilege that best reflects the audit results.

User and account management tools are also essential when implementing the principle of least privilege. Regularly reviewing and removing unused or unnecessary accounts reduces the potential targets for an attacker. Similarly, temporary privileges, which grant additional access rights for a limited time and only when required, can help keep privileges as restrictive as possible.

Another practical approach to restricting access is using role-based access control (RBAC). RBAC assigns system access rights based on predefined roles, and each role has a carefully defined set of permissions that match the requirements of any particular role within the organization. This approach ensures that users have just enough access to perform their tasks but nothing more.

The principle of least privilege also applies to software applications and operating systems, not just to users. For instance, ensuring that applications run with the minimum necessary permissions can prevent them from being exploited to carry out privileged actions.

### Access Control Lists

Access control lists (ACLs) in computer systems and networks are used to enforce access control policies. An ACL is a list of rules or entries that specify which users or groups are allowed or denied access to specific resources or perform certain actions. In networks, ACLs are associated with routers, firewalls, or similar devices and define rules that determine how network traffic is filtered or forwarded based on criteria like source IP addresses, destination IP addresses, ports, or protocols.

ACLs can help to control network access and protect against unauthorized or malicious activities. ACLs control access to files, directories, or system resources in operating systems and file systems. Each access control entry (ACE) typically contains a user or group identifier and associated permissions controlling actions that are allowed or denied. These permissions often include read, write, execute, and sometimes more granular limits such as modify, delete, or list.

While ACLs offer flexibility and control, managing complex access control policies with numerous ACL entries can become challenging. Complexity increases the risk of misconfigurations. Therefore, proper planning, periodic reviews, and best practice configurations are essential when implementing and maintaining ACLs.

### File System Permissions

With file system security, each object in the file system has an access control list (ACL) associated with it. The ACL contains a list of accounts (principals) allowed to access the resource and the permissions they have over it. The order of ACEs in the ACL is important in determining effective permissions for a given account. ACLs can be enforced by a file system that supports permissions, such as NTFS, ext3/ext4, or ZFS.

![A Screengrab of a window titled, permission entry for LABFILES.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/8352-1692974870870.png) Description

Configuring an access control entry for a folder. (Screenshot used with permission from Microsoft.)

For example, in Linux, there are three basic permissions:

- **Read (****r****)** —is the ability to access and view the contents of a file or list the contents of a directory.
- **Write (****w****)** —is the ability to save changes to a file, or create, rename, and delete files in a directory (also requires execute).
- **Execute (****x****)** —is the ability to run a script, program, or other software file, or the ability to access a directory, execute a file from that directory, or perform a task on that directory, such as file search.

These permissions can be applied in the context of the owner user (u), a group account (g), and all other users/world (o). A permission string lists the permissions granted in each of these contexts:

d rwx r-x r-x home

The string above shows that for the directory (d), the owner has read, write, and execute permissions, while the group context and other users have read and execute permissions.

The chmod command is used to modify file permissions in Unix/Linux systems. It can be used in symbolic mode or absolute mode. In symbolic mode, the command works as follows:

chmod g+w, o-x home

The effect of this command is to append write permission to the group context and remove execute permission from the other context. By contrast, the command can also be used to replace existing permissions. For example, the following command applies the configuration shown in the first permission string, which sets the permissions to rwxr-xr-x:

chmod u=rwx,g=rx,o=rx home.

In absolute mode, permissions are assigned using octal notation, where r=4, w=2. and x=1. For example, the following command has the same effect:

chmod 755 home

In this example, the 755 correlates to the permissions assigned to the user, group, and others, where user permissions are represented by 7, group permissions are 5, and others are also 5. The numbers are generated by adding the values associated with r (read), w (write), and x (execute). The only combination of values that can result in 7 is 4+2+1 or r, w, x. Similarly, the only combination of values resulting in 5 is 4+1, or r,x. This means that the owner has r,w, and x whereas the group and others have only r and x.

### Application Allow Lists and Block Lists

One element of endpoint configuration is an execution control policy that defines applications that can or cannot be run.

- An allow list (or approved list) denies execution unless the process is explicitly authorized.
- A block list (or deny list) generally allows execution but explicitly prohibits listed processes.

The contents of allow lists and block lists needs to be updated in response to incidents and ongoing threat hunting and monitoring.

Threat hunting may also provoke a strategic change. For example, if you rely principally on explicit denies, but your systems are subject to numerous intrusions, you will have to consider adopting a "least privileges" model and using a deny-unless-listed approach. This sort of change can be highly disruptive, however, so it must be preceded by a risk assessment and business impact analysis.

Execution control can also be tricky to configure effectively, with many opportunities for threat actors to evade the controls. Detailed analysis of the attack might suggest the need for changes to the existing mechanism or for a more robust system.

### Monitoring

Monitoring plays a vital role in endpoint hardening, helping enforce and maintain the security measures put in place during the hardening process. Once devices are hardened, monitoring helps ensure these conditions remain in place.

Security analysts can detect changes that weaken the hardened configuration through continuous monitoring. For instance, if a previously disabled port is detected as open or a service that was disabled is changed to enabled, monitoring tools can alert analysts of the change—which may indicate a breach.

Additionally, monitoring can provide valuable data for compliance and auditing purposes. Regular reports on the status of endpoint devices can verify that hardening baselines have been effectively deployed and maintained, supporting compliance with various regulations and industry standards.

### Configuration Enforcement

Configuration enforcement describes methods used to ensure that systems and devices within an organization's network adhere to mandatory security configurations. Configuration enforcement generally depends upon a few important capabilities.

- **Standardized Configuration Baselines** are defined by organizations like NIST, CIS, or the organization itself and used as the benchmark for how systems and devices should be configured.
- **Automated Configuration Management Tools** are used to apply and maintain standardized configuration baselines across the environment automatically.
- **Continuous Monitoring and Compliance Checks** are crucial to detect deviations from mandatory configurations.
- **Change Management** processes ensure configuration changes are properly reviewed, tested, and approved before implementation.

Managing firewall rules across an organization's network is a practical example of a configuration setting that can benefit from configuration enforcement. An organization can use an automated configuration management tool to ensure device firewalls are correctly configured, including blocking all incoming traffic by default and only allowing specific, necessary connections. Continuously monitoring detects any changes and automatically reverts them to enforce the secure, approved configuration.

Additionally, regular compliance checks ensure that firewalls adhere to approved configuration settings, and any changes need to be reviewed and approved via proper change management processes prior to implementation.

### Group Policy

Group Policy is a feature of the Microsoft Windows operating system and provides centralized management and configuration of operating systems, applications, and user settings in an Active Directory environment. Group Policies enforce security settings, such as those mandated in a baseline, by applying consistent settings across all systems linked to specific Group Policies. In general terms, Group Policies are linked to containers called Organizational Units (OUs) that normally contain user and computer objects. The Group Policies linked to the OU apply to all objects contained within it.

Examples of common Group Policy settings include password policies, user rights, Windows Firewall settings, system update settings, software installation restrictions, and many others. Applying settings centrally using Group Policy reduces potential issues related to misconfigurations or inconsistent settings.

### SELinux

SELinux is a security feature of the Linux kernel that supports access control security policies, including mandatory access controls (MAC). SELinux allows more granular permission control over every process and system object within an operating system, strictly limiting the resources a process can access and what operations it can perform. SELinux operates on the principle that if a process or user does not need resource access to operate, it will be blocked to isolate applications better, restrict system and file access, and prevent malicious or flawed programs from causing harm to the system. SELinux capabilities are also available on the Android operating system [https://source.android.com/docs/security/features/selinux](https://source.android.com/docs/security/features/selinux). Due to the significant architectural differences between Linux and Android, SELinux capability on Android is enabled using SEAndroid to provide similar functionality but using a separately maintained codebase.