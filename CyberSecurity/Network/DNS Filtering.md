Domain Name System (DNS) filtering is a technique that blocks or allows access to specific websites by controlling the resolution of domain names into IP addresses. It operates on the principle that for a device to access a website, it must first resolve its domain name into its associated IP address, a process managed by DNS. When a request is made to resolve a website URL, the DNS filter checks the request against a database of domain names. If the domain is associated with malicious activities or is on an unapproved list for any reason, the filter blocks the request, preventing access to the potentially harmful website.

DNS filtering is highly effective for many reasons. A few are listed below:

- It provides a proactive defense mechanism, blocking access to known phishing sites, malware distribution sites, and other malicious online destinations.
- It can help enforce an organization's acceptable use policies (AUPs) by blocking access to inappropriate or distracting websites and ensuring that the Internet is used responsibly and productively.
- It can protect all devices connected to a network, including IoT devices, providing an extra layer of security.
- It is a simple solution that is easy to implement and presents minimal risk, making it a cost-effective security control suitable for networks of any size.

While DNS filtering is highly effective, it must be combined with other security measures for comprehensive protection.

### Implementing DNS Filtering

DNS filtering is implemented using different methods and tools. A prevalent method is through DNS filtering services like Cisco's OpenDNS ([https://www.opendns.com/](https://www.opendns.com/)), Quad9 ([https://www.quad9.net/](https://www.quad9.net/)), or CleanBrowsing ([https://cleanbrowsing.org/](https://cleanbrowsing.org/)). These services provide DNS resolution with built-in filtering, simply requiring organizations and users to redirect their DNS requests to the filtering service's DNS servers.

Organizations that manage their own DNS servers, such as Microsoft's DNS server or BIND, can directly implement DNS filtering. This method, albeit more complex, provides complete control over filtering policies and permits the integration of block lists or Response Policy Zone (RPZ) feeds into server configurations.

Another strategy involves using DNS firewalls, which intercept DNS queries at the network level and apply filtering rules accordingly. Some endpoint protection tools and antivirus software provide DNS filtering capabilities to provide device-level protection ideal for laptops and other mobile devices that may connect to numerous networks with varying levels of security enabled by default.

Open source Pi-hole ([https://pi-hole.net/](https://pi-hole.net/)) or ADGuard ([https://github.com/AdguardTeam/AdguardHome](https://github.com/AdguardTeam/AdguardHome)) software can be configured as a local DNS resolver with filtering capabilities. This software runs on Linux and is commonly implemented using Raspberry Pi hardware due to its low-performance overhead. Regardless of the method chosen, customization of filtering policies allows for categorizing websites to simplify the creation of block lists or allow lists per requirements. Keeping DNS filters updated is essential to effective DNS filtering to keep pace with evolving threats and changing organizational needs.

![A Screengrab of the Pi-hole dashboard.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/7215-1692974871781.png) Description

Status is displayed at the top-left. Dashboard option is selected from the options in the left pane. The dashboard displays total queries (5 clients): 3416, queries blocked: 491, percent blocked: 14.4 percent, and domains on blocklist: 82,309. Two vertical bar graphs are titled total queries over last 24 hours and client activity over last 24 hours.

The Pi-hole administrative dashboard showing DNS resolution statistics. (Screenshot courtesy of Pi-hole.)

### DNS Security

DNS is a critical service that should be configured to be fault tolerant. DoS attacks are hard to perform against the servers that perform Internet name resolution, but if an attacker can target the DNS server on a private network, it is possible to seriously disrupt the operation of that network.

To ensure DNS security on a private network, local DNS servers should only accept recursive queries from local hosts (preferably authenticated local hosts) and not from the Internet. You also need to implement access control measures on the server to prevent a malicious user from altering records manually. Similarly, clients should be restricted to using authorized resolvers to perform name resolution.

Attacks on DNS may also target the server application and/or configuration. Many DNS services run on BIND (Berkley Internet Name Domain), distributed by the Internet Systems Consortium ([isc.org](https://www.isc.org/)). There are known vulnerabilities in many versions of the BIND server, so it is critical to patch the server to the latest version. The same general advice applies to other DNS server software, such as Microsoft's. Obtain and check security announcements and then test and apply critical and security-related patches and upgrades.

DNS footprinting means obtaining information about a private network by using its DNS server to perform a zone transfer (all the records in a domain) to a rogue DNS or simply by querying the DNS service, using a tool such as nslookup or dig. To prevent this, you can apply an access control list to prevent zone transfers to unauthorized hosts or domains, to prevent an external server from obtaining information about the private network architecture.

DNS Security Extensions (DNSSEC) help to mitigate against spoofing and poisoning attacks by providing a validation process for DNS responses. With DNSSEC enabled, the authoritative server for the zone creates a "package" of resource records (called an RRset) signed with a private key (the Zone Signing Key). When another server requests a secure record exchange, the authoritative server returns the package along with its public key, which can be used to verify the signature.

The public Zone Signing Key is itself signed with a separate Key Signing Key. Separate keys are used so that if there is some sort of compromise of the Zone Signing Key, the domain can continue to operate securely by revoking the compromised key and issuing a new one.

![A Screengrab of the DNS Manager.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/5670-1692974871919.png) Description

The tabs at the top are: file, action, view, and help. The option classroom dot local under the folder forward lookup zones folder is selected from the left pane. The right pane shows a table that lists the name, type, data, and timestamp.

Windows Server DNS services with DNSSEC enabled. (Screenshot used with permission from Microsoft.)

The Key Signing Key for a particular domain is validated by the parent domain or host ISP. The top-level domain trusts are validated by the Regional Internet Registries and the DNS root servers are self-validated, using a type of M-of-N control group key signing. This establishes a chain of trust from the root servers down to any particular subdomain.