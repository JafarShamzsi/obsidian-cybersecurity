After an incident has been contained, the eradication process applies mitigation techniques and controls to remove the intrusion tools and unauthorized configuration changes from systems.

When traces of malware, backdoors, and compromised accounts have been eliminated, the recovery process ensures restoration of capabilities and services. This means that hosts are fully reconfigured to operate the business workflow they were performing before the incident. An essential part of recovery is the process of ensuring that the system cannot be compromised through the same attack vector, or failing that, that the vector is closely monitored to provide advance warning of another attack.

Eradication of malware or other intrusion mechanisms and recovery from the attack will involve several steps:

1. **Reconstitution of affected system**—by either removing the malicious files or tools from affected systems or restoring the systems from secure backups/images.

If reinstalling from baseline template configurations or images, make sure that there is nothing in the baseline that allowed the incident to occur! If so, update the template before rolling it out again.

2. **Reaudit security controls**—by ensuring they are not vulnerable to another attack. This could be the same attack or from some new attack that the attacker could launch through information they have gained about the network.

If the organization is subjected to a targeted attack, be aware that one incident may be very quickly followed by another.

3. Ensure that affected parties are notified and provided with the means to remediate their own systems. For example, if customers' passwords are stolen, they should be advised to change the credentials for any other accounts where that password might have been used (not good practice, but most people do it).