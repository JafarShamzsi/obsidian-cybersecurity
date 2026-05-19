Following detection and analysis, the incident management database should have a record of the event indicators, the nature of the incident, its impact, and the investigator responsible for managing the case. The next phase of incident management is to determine an appropriate response.

As incidents cover a wide range of different scenarios, technologies, motivations, and degrees of seriousness, there is no standard approach to containment or incident isolation. Some of the many complex issues facing the CIRT are the following:

- What damage or theft has occurred already? How much more could be inflicted and in what sort of time frame (loss control)?
- What countermeasures are available? What are their costs and implications?
- What actions could alert the threat actor that the attack has been detected? What evidence of the attack must be gathered and preserved?
- What notification or reporting is required at this stage of the incident?

Containment techniques can be classed as either isolation-based or segmentation-based.

### Isolation-Based Containment

Isolation involves removing an affected component from whatever larger environment it is a part of. This can be everything from removing a server from the network after it has been the target of a denial of service attack to placing an application in a sandbox outside the host environments it usually runs on. Isolation removes any interface between the affected system and the production network or the Internet.

A simple option is to disconnect the host from the network by pulling the network plug (creating an air gap) or disabling its switch port. This is the least stealthy option and will reduce opportunities to analyze the attack or malware.

If a group of hosts is affected, you could use routing infrastructure to isolate one or more infected virtual LANs (VLANs) in a sinkhole that is not reachable from the rest of the network. Another possibility is to use firewalls or other security filters to prevent infected hosts from communicating.

Finally, isolation could also refer to disabling a user account or application service. Temporarily disabling users' network accounts may prove helpful in containing damage if an intruder is detected within the network. Without privileges to access resources, an intruder will not be able to further damage or steal information from the organization. Applications that you suspect may be the vector of an attack can be much less effective to the attacker if the application is prevented from executing on most hosts.

### Segmentation-Based Containment

Segmentation-based containment is a means of achieving the isolation of a host or group of hosts using network technologies and architecture. Segmentation uses VLANs, routing/subnets, and firewall ACLs to prevent a host or group of hosts from communicating outside the protected segment. As opposed to completely isolating the hosts, you might configure the protected segment as a sinkhole or honeynet and allow the attacker to continue to receive filtered (and possibly modified) output to deceive them into thinking the attack is progressing successfully. This facilitates analysis of the threat actor's TTPs and, potentially, their identity. Attribution of the attack to a particular group will allow an estimation of adversary capability.