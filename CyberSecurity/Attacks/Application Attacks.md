An **application attack** targets a vulnerability in OS or application software. An application vulnerability is a design flaw that can cause the application security system to be circumvented or that will cause the application to crash. There are broadly two main scenarios for application attacks:

- Compromising the operating system or third-party apps on a network host by exploiting Trojans, malicious attachments, or browser vulnerabilities. This allows the threat actor to obtain a foothold on a local network.
- Compromising the security of a website or web application. This allows a threat actor to gain control of a web host, and either steal data from it or use it to try to penetrate further into the network.

Increased numbers of application crashes and errors might provide a general indicator that a threat actor is attempting to exploit a vulnerability in a network service, desktop OS or app, or web application. Errors might be recorded in a system log or application-specific log, depending on the nature of the software and the type of fault event. Anomalous CPU, memory, storage, or network utilization can also be an indicator of application attack. These indicators can also have multiple non-malicious causes, however, so it is important to correlate them to factors that identify specific types of application attacks.

### Privilege Escalation

The purpose of most application attacks is to allow the threat actor to run their own code on the system. This is referred to as arbitrary code execution. Where the code is transmitted from one machine to another, it can be referred to as remote code execution. The code would typically be designed to install some sort of backdoor or to disable the system in some way.

An application or process must have privileges to read and write data and execute functions. Depending on how the software is written, a process may run using a system account, the account of the logged-on user, or a nominated account. If a software exploit works, the attacker may be able to execute arbitrary code with the same privilege level as the exploited process. There are two main types of privilege escalation:

- Vertical privilege escalation (or elevation) is where a user or application can access functionality or data that should not be available to them. For instance, a process might run with local administrator privileges, but a vulnerability allows the arbitrary code to run with higher SYSTEM privileges.
- Horizontal privilege escalation is where a user accesses functionality or data that is intended for another user. For instance, via a process running with local administrator privileges on a client workstation, the arbitrary code is able to execute as a domain account on an application server.

Without performing detailed analysis of code or process execution in real time, it is privilege escalation that provides the simplest indicator of an application attack. If process logging has been configured, the audit log can provide evidence of privilege escalation attempts. These attempts may also be detected by incident response and endpoint protection agents, which will display an alert.

### Buffer Overflow

A buffer is an area of memory that an application reserves to store some value. The application will expect the data to conform to some expected value size or format. To exploit a buffer overflow vulnerability, the attacker passes data that deliberately fills the buffer to its end and then overwrites data at its start. One of the most common vulnerabilities is a stack overflow. The stack is an area of memory used by a program subroutine. It includes a return address, which is the location of the program that called the subroutine. An attacker could use a buffer overflow to change the return address, allowing the attacker to run arbitrary code on the system.

Operating systems use mechanisms such as address space layout randomization (ASLR) and Data Execution Prevention (DEP) to mitigate risks from buffer overflow. Failed attempts at buffer overflow can be identified through frequent process crashes and other anomalies.