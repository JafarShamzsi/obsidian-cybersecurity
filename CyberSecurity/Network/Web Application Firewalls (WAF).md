A **Web Application Firewall (WAF)** is a security appliance or software designed to protect web applications by filtering, monitoring, and blocking HTTP/S traffic to and from a web service. WAFs are specialized intrusion detection/prevention systems that focus on application-layer (Layer 7) attacks, such as injection, cross-site scripting (XSS), and denial-of-service attempts that target web applications and their associated databases.

---

## Purpose and Functionality

WAFs protect web-facing services by:

- Blocking **malicious HTTP/S traffic** using signature-based or behavior-based filtering.
- Mitigating **code injection attacks** (e.g., SQLi, XSS, command injection).
- Enforcing **application-specific security policies**.
- Identifying and logging **application-level threats**.
- Protecting against **automated bots, scanners**, and **web scraping**.
- Preventing **unauthorized access attempts** and **exfiltration of data**.

---

## Core Features

- **Application-aware filtering**: Understands and inspects HTTP/S traffic payloads at Layer 7.
- **Signature-based detection**: Blocks known exploits using rule sets like the OWASP Core Rule Set (CRS).
- **Pattern and anomaly detection**: Identifies deviations from expected traffic behavior.
- **Logging and alerting**: Detailed event logs with source IP, requested URL, detected rule, and payload.
- **Virtual patching**: Blocks known vulnerabilities in web applications before they are formally patched.
- **DDoS mitigation**: Can enforce rate-limiting or CAPTCHA challenges for suspected flooding.
![[3290-1692974865220.png]]
---

## Deployment Models

1. **Inline Appliance**  
   - Positioned between the client and the web server.
   - All inbound/outbound traffic passes through the WAF.
   - May introduce latency but enables real-time blocking.

2. **Reverse Proxy (Common)**  
   - WAF acts as an intermediary that forwards valid traffic to the web server.
   - Hides the internal structure and IP of the application server.
   - Enables SSL termination and caching.

3. **Plug-in/Module (Integrated)**  
   - Embedded within the web server (e.g., Apache, IIS, NGINX).
   - Example: **ModSecurity** is a popular WAF engine that integrates into web server platforms.
   - Lower overhead but shares resources with the web server process.

4. **Cloud-based WAF**  
   - Delivered as a managed service (e.g., AWS WAF, Cloudflare WAF).
   - Easily scalable, globally distributed, and integrates with CDNs.
   - Suitable for organizations with limited on-premises infrastructure.

---

## Example: ModSecurity WAF

ModSecurity is a popular open-source WAF that can be integrated with web servers such as Apache, NGINX, or IIS.

- Default rule sets can generate extensive logging, including benign or low-severity events.
- Example event logged in Windows IIS:
  - Event Viewer > Application Logs
  - Source: ModSecurity
  - Action: Detected scanning attempt
  - Output includes payload analysis, matched rule ID, and the detection engine used.

This enables administrators to respond to incidents and fine-tune rules to reduce false positives.

---

## Benefits

- **Enhanced security for web apps** without modifying the app codebase.
- **Granular control** over HTTP methods, URIs, headers, cookies, and body content.
- **Visibility into attacks** targeting business logic or specific app features.
- **Compliance support** (e.g., PCI DSS requires WAF protection for public-facing web apps).

---

## Limitations

- **False positives**: Aggressive rules may block legitimate users.
- **Maintenance overhead**: Rule tuning and log analysis are ongoing requirements.
- **Latency**: Inline WAFs may introduce network delays.
- **Not a substitute for secure coding**: WAFs complement but do not replace application-layer security best practices.

---

## Use Cases

- **E-commerce sites** facing carding attacks or SQLi attempts.
- **Web portals** subject to user input and complex session logic.
- **APIs and microservices** exposed over HTTP/S.
- **Legacy web applications** with unpatched vulnerabilities.

---

## Related Topics

- [[Intrusion Detection and Prevention Systems (IDPS)]]
- [[Reverse Proxy and Forward Proxy]]
- [[Application Security Testing (DAST/SAST)]]
- [[Content Delivery Networks (CDNs)]]
- [[TLS Offloading and SSL Termination]]

