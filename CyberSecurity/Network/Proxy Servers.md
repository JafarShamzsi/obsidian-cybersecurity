
A **proxy server** is an intermediary between clients and destination services. It acts on behalf of clients (forward proxy) or services (reverse proxy), implementing security, performance, and access control mechanisms. Proxies commonly operate at **Layer 7 (Application Layer)** of the OSI model and can perform **deep packet inspection**, **header rewriting**, **URL filtering**, and **content caching**.

Proxies provide better application-layer visibility than traditional packet filters or even basic stateful firewalls.
![[1446-1692974864724.png]]
---

## Forward Proxy Servers

A **forward proxy** manages **outbound** traffic from clients inside a trusted network to external resources (e.g., the Internet).

### Core Characteristics

- Acts on behalf of internal clients.
- Enforces protocol-specific policies (commonly HTTP, HTTPS, FTP, SMTP).
- Filters based on **URL**, **domain name**, **content type**, and **application behavior**.
- Can cache responses to reduce bandwidth and improve latency.

### HTTP and HTTPS Proxy Behavior

- Intercepts client traffic bound for TCP/80 (HTTP) and TCP/443 (HTTPS).
- In HTTPS scenarios, the proxy often implements **SSL interception** via **certificate spoofing**, enabling inspection of encrypted payloads.
  - Requires clients to trust the proxy's CA certificate.

### Proxy Packet Handling

Depending on configuration:
- May **rebuild** headers (e.g., HTTP headers).
- May **sanitize** payloads (e.g., strip malicious code or disallowed elements).
- May **block or rewrite** requests based on ACLs, MIME types, referrers, or user-agent strings.

---
![[3363-1692974864790.png]]
## Proxy Types by Transparency

### Non-Transparent Proxy

- Clients are explicitly configured to use the proxy IP and port (typically TCP/8080).
- Configuration can be manual or automated via:
  - **PAC (Proxy Auto-Configuration) script**
  - **WPAD (Web Proxy Auto-Discovery Protocol)**

### Transparent Proxy (Intercepting Proxy)

- No client configuration required.
- Proxy intercepts traffic automatically, often via Layer 2 or Layer 3 techniques:
  - WCCP (Web Cache Communication Protocol)
  - Policy-Based Routing (PBR)
  - Inline deployment

- Proxy rewrites TCP sessions to itself and can decrypt HTTPS using its own CA certificate.
- Often used for:
  - Enforcing web access policies
  - Blocking malicious domains
  - Logging user behavior

> **Note:** Transparent proxies must be deployed carefully to avoid violating user privacy and legal constraints.

---

## Proxy Authentication

Proxies may enforce access controls via:
- **Basic or NTLM authentication**
- **Kerberos/SPNEGO** for **Single Sign-On (SSO)** using corporate Active Directory credentials
- LDAP or RADIUS integration

This ensures only authorized users can access filtered or external content.

---

## Web Caching

A common function of proxies is **caching** web content. Benefits include:
- Reduced bandwidth usage
- Faster page loads for frequently visited content
- Less load on origin servers

Caching is especially useful for static content and frequently accessed websites.

Caching rules may include:
- Expiration headers (e.g., Cache-Control, ETag)
- Policy-based TTLs
- Blacklists/whitelists for cache bypassing

---

## Proxy Server Examples

### OPNsense Web Proxy (Forward Proxy)

- Implements a **caching proxy** using `squid`.
- Supports both non-transparent and transparent modes.
- Can apply **ACLs** to:
  - Block specific **IP addresses**
  - Block **domains** and **URLs**
  - Enforce **user/group policies**

#### Example Use Case

> An organization uses OPNsense to restrict access to social media websites, inspect HTTPS traffic, and cache static content to reduce load on its outbound Internet link.

---

## Reverse Proxy Servers

A **reverse proxy** handles **inbound** connections from external clients to internal application servers. The proxy:
- Appears as the endpoint to the client
- Performs TLS termination, caching, and content filtering
- Forwards validated traffic to internal web servers

### Benefits

- **Hides internal topology** (clients never interact directly with origin servers)
- Protects applications from direct attack
- Load balancing across multiple backend servers
- TLS offloading and Web Application Firewall (WAF) integration

### Typical Usage

Deployed at the **network perimeter**, between the DMZ and Internet.

#### Example Use Case

> A reverse proxy is deployed to inspect inbound HTTPS traffic to a corporate web server. It terminates TLS, filters requests against OWASP Top 10 vulnerabilities, and passes sanitized traffic to the backend over HTTP.

---

## Security Features in Proxies

| Feature                  | Description |
|--------------------------|-------------|
| ACL Filtering            | Enforces allow/deny rules based on IP, domain, user, time-of-day, etc. |
| Content Inspection       | Analyzes HTTP headers and body for policy violations or malware. |
| SSL Interception         | Decrypts HTTPS traffic to apply rules, then re-encrypts for forwarding. |
| Authentication           | Verifies user identity before permitting traffic. |
| Anonymity Control        | Blocks anonymizers and enforces identity-based filtering. |
| Logging & Auditing       | Logs user activity, accessed URLs, and violations for SIEM analysis. |

---

## Proxy Auto-Configuration (PAC) and WPAD

### PAC Files

A **Proxy Auto-Config (PAC)** file is a JavaScript-based configuration file that defines rules for selecting the appropriate proxy for a given URL.

Example:
```javascript
function FindProxyForURL(url, host) {
  if (shExpMatch(host, "*.internal.local")) {
    return "DIRECT";
  }
  return "PROXY 192.168.1.1:8080";
}
```

### WPAD

**Web Proxy Auto-Discovery Protocol (WPAD)** allows clients to automatically locate a PAC file:

- Uses **DHCP Option 252** or **DNS SRV records**
    
- Risk of WPAD spoofing if network DNS/DHCP is compromised
    

> **Security Note:** WPAD must be carefully managed to avoid man-in-the-middle attacks or rogue proxy configurations.

---

## Proxy Architecture Overview

```
[ Client ] <--> [ Forward Proxy ] <--> [ Internet Services ]
                              |
[ Internet Clients ] <--> [ Reverse Proxy ] <--> [ Internal Web Servers ]

```
