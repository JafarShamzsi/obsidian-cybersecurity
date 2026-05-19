The Simple Network Management Protocol (SNMP) is a widely used framework for management and monitoring. SNMP consists of an SNMP monitor and agents.

- The agent is a process (software or firmware) running on a switch, router, server, or other SNMP-compatible network device.
- This agent maintains a database called a management information base (MIB) that holds statistics relating to the activity of the device (for example, the number of frames per second handled by a switch). The agent is also capable of initiating a trap operation where it informs the management system of a notable event (port failure, for instance). The threshold for triggering traps can be set for each value. Device queries take place over port 161 (UDP); traps are communicated over port 162 (also UDP).
- The SNMP monitor (a software program) provides a location from which network activity can be overseen. It monitors all agents by polling them at regular intervals for information from their MIBs and displays the information for review. It also displays any trap operations as alerts for the network administrator to assess and act upon as necessary.

If SNMP is not used, it should be disabled. When running SNMP, the following includes some important guidelines:

- SNMP community names are sent in plaintext and so should not be transmitted over the network if there is any risk that they could be intercepted.
- Use difficult-to-guess community names; never leave the community name blank or set to the default.
- Use access control lists to restrict management operations to known hosts (that is, restrict to one or two host IP addresses).
- Use SNMP v3 whenever possible, and disable older versions of SNMP. SNMP v3 supports encryption and strong user-based authentication. Instead of community names, the agents are configured with a list of usernames and access permissions. When authentication is required, SNMP messages are signed with a hash of the user's passphrase. The agent can verify the signature and authenticate the user using its own record of the passphrase.