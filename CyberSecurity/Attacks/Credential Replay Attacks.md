A threat actor might establish a foothold on the network by compromising a single workstation via malware or a password attack. Once an initial foothold has been gained, the threat actor's objective is likely to be to identify data assets. For this, they need to find ways to perform lateral movement to compromise other hosts on the network, and privilege escalation to gain more permissions over network assets. To accomplish these objectives, as well as cracking more passwords or finding more vulnerabilities, they can use **credential replay** attacks.

In terms of network attacks, credential replay attacks mostly target Windows Active Directory networks. There are also credential replay attacks that target web applications. We will discuss these in the next topic.

If a user account on a Windows host has authenticated to an Active Directory domain network, the Local Security Authority Subsystem Service (LSASS) caches various secrets in memory and in the Security Account Manager (SAM) registry database to facilitate single sign-on. These secrets include the following:

- Kerberos Ticket Granting Ticket (TGT) and session key. This allows the host to request service tickets to access applications.
- Service tickets for applications where the user has started a session.
- NT hash of local and domain user and service accounts that are currently signed in, whether interactively or remotely over the network. Early Windows business networks used NT LAN Manager (NTLM) challenge and response authentication. While the NTLM protocol is deprecated for most uses, the NT hash is still used as the credential storage format. The NT hash is used where legacy NTLM authentication is still allowed, and can be involved in signing Kerberos requests and responses.

Critical for network security, if different users are signed in on the same host, secrets for all these accounts could be cached by LSASS. If some of these accounts are for more privileged users, such as domain administrators, a threat actor might be able to use the secrets to escalate privileges.

LSASS purges hashes from memory within a few minutes of the user signing out. The SAM database caches local and Microsoft account credentials, but not domain credentials. Some editions of Windows implement a virtualization feature called Credential Guard to protect these secrets from malicious processes, even if they have SYSTEM permissions.

Credential replay attacks use various mechanisms to obtain and exploit these locally stored secrets to start authenticated sessions on other hosts and applications on the network. For example, if a threat actor can obtain an NT hash, they can use a pass the hash (PtH) attack to start a session on another host if that host is running a service such as file sharing or remote desktop that still allows NTLM authentication.

![An illustrations shows the pass the hash process.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/4211-1692974875410.png)Description

The process involves four steps as follows:

1. Victim logs on. DC verifies user with Kerberos.

2. Victim logs on again. Kerberos credentials cached in LSASS process memory.

3. Attacker dumps LSASS memory on victim's computer. Cached credentials revealed.

4. Attacker uses hash on other computer. Hashed credentials recognized by Kerberos.

The pass the hash process. The Security Accounts Manager (SAM) is a Windows registry database that stores local account credentials. (Images © 123RF.com.)

Legacy NTLM authentication is often disabled as it is such a high security risk. Other types of credential replay are directed against Kerberos authentication and authorization. For example, a golden ticket attack attempts to forge a ticket granting ticket. If successful, this gives the threat actor effectively unrestricted access to all domain resources. A silver ticket attack attempts to forge service tickets. These can be described as pass the ticket (PtT) attacks.

Microsoft has released a number of mitigations against these specific credential replay attacks. Ensuring hosts are fully patched and use secure configuration baselines greatly reduces their effectiveness. Where they remain a risk, a detection system can be configured to correlate a sequence of security log events, but this method can be prone to false positives. Antivirus and host-based intrusion detection can often detect the malware code used to dump credentials or launch ticket forgery attacks.