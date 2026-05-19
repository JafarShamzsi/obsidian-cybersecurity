A secure baseline is a collection of standard configurations and settings for network devices, software, patching and updates, access controls, logging, monitoring, password policies, encryption, endpoint protection, and many others. Secure baselines improve information technology security, manageability, and operational efficiencies by establishing consistent and centralized rules and procedures regarding configuring and securing the environment.

The [Center for Internet Security (CIS)](https://www.cisecurity.org) Benchmarks are an important resource for secure configuration best practices. CIS is recognized globally for publishing and maintaining best practice guides for securing IT systems and data. [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) cover multiple domains, such as networks, operating systems, and applications, and are updated continuously in response to evolving risks. For example, there are benchmarks for compliance with IT frameworks and compliance programs, such as PCI DSS, NIST 800-53, SOX, and ISO 27000. There are also product-focused benchmarks, such as for Windows Desktop, Windows Server, macOS, Linux, Cisco, web browsers, web servers, database and email servers, and VMware ESXi. [Security Technical Implementation Guides (STIGs)](https://public.cyber.mil/stigs/) are a specific secure baseline developed by the [Defense Information Systems Agency (DISA)](https://disa.mil/) for the US Department of Defense. Like CIS Benchmarks, STIGs define a standardized set of security configurations and controls specifically designed for the DoD's IT infrastructure.

Several tools and technologies are available to help manage, deploy, and measure compliance with established secure baselines. Configuration management tools, such as [Puppet](https://www.puppet.com/), [Chef](https://www.chef.io/), [Ansible](https://www.ansible.com/), and Microsoft's Group Policy, allow organizations to automate the deployment of secure baseline configurations across various diverse systems. These tools help enforce consistency and detect and correct deviations from the established baseline. For monitoring compliance, Security Content Automation Protocol (SCAP) compliant tools, like [OpenSCAP](https://www.open-scap.org/), can assess and verify the system's adherence to the baseline. Furthermore, the CIS provides the [CIS-CAT Pro tool](https://www.cisecurity.org/cybersecurity-tools/cis-cat-pro), designed to assess system configurations against CIS's secure baseline benchmarks. The [SCAP Compliance Checker (SCC)](https://public.cyber.mil/stigs/scap/) is a tool maintained by the DISA used to measure compliance with STIG baselines.

### Hardening Concepts

Network equipment, software, and operating systems use default settings from the developer or manufacturer which attempt to balance ease of use with security. Default configurations are an attractive target for attackers as they usually include well-documented credentials, allow simple passwords, use insecure protocols, and many other problematic settings. By leaving these default settings in place, organizations increase the likelihood of successful cyberattacks. Therefore, it's crucial to change these default settings to improve security.

Hardening describes the methods to improve a device's security by changing its default configuration, often by implementing the recommendations in published secure baselines.

### Switches and Routers

Examples of changes designed to improve the security of switches and routers from the default settings include the following:

- **Change Default Credentials** that are well documented and pose a significant security risk.
- **Disable Unnecessary Services and Interfaces** on a switch or router. Not every service or interface is needed. For example, services like HTTP or Telnet should be avoided.
- **Use Secure Management Protocols** such as SSH instead of Telnet or HTTPS instead of HTTP.
- **Implement Access Control Lists (ACLs)** to restrict access to the router or switch to only required devices and networks.
- **Enable Logging and Monitoring** to help identify issues like repeated login failures, configuration changes, and many others.
- **Configure Port Security** helps limit the devices that can connect to a switch port to prevent unauthorized access.
- **Strong Password Policies** help reduce the risk of password attacks.
- **Physically Secure Equipment** like keeping devices in a locked room to prevent unauthorized physical access.

### Server Hardware and Operating Systems

Examples of changes designed to improve the security of servers from the default settings include the following:

- **Change Default Credentials** to prevent unauthorized access, similar to network devices.
- **Disable Unnecessary Services** to reduce the attack surface of the server. Each service running on a server represents a potential point of entry for an attacker.
- **Apply Software Security Patches and Updates Regularly** to fix known vulnerabilities and provide security improvements. Automated patch management ensures this process is consistent and timely.
- **Least Privilege Principle** limits each user to the least amount of privilege necessary to perform a function to reduce the impact of a compromised account.
- **Use Firewalls and Intrusion Detection Systems (IDS)** to help block or alert on malicious activity.
- **Secure Configuration** of servers should use baseline configurations such as those provided by the CIS or STIGs.
- **Strong Access Controls** include strong password policies, multifactor authentication (MFA), and privileged access management (PAM).
- **Enable Logging and Monitoring** to help identify issues like repeated login failures, configuration changes, and many others similar to the benefits for network equipment.
- **Use Antivirus and Antimalware Solutions** to detect and quarantine malware automatically.
- **Physical Security** of server equipment racks, server rooms, or datacenters prevents unauthorized access.