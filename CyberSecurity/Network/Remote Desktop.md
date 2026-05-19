**Remote Desktop** refers to the ability to control a computing device from a remote location over a network. This is achieved by transmitting user input (keyboard, mouse) from the client to the host, and streaming output (display, audio) back from the host to the client.

There are two primary models of remote access:

- **Remote Access VPN**: Connects a device to an entire remote **private network** via a secure tunnel.
- **Remote Desktop Access**: Connects a client to a **specific host or virtual desktop**, often for administrative or productivity purposes.

---

## Remote Desktop Protocol (RDP)

**RDP (Remote Desktop Protocol)** is a proprietary protocol developed by Microsoft that allows remote GUI access to Windows systems.

### Features:
- Encrypted by default (TLS-based encryption)
- Supports audio redirection, clipboard sharing, drive mapping, and printer access
- GUI-based session for a one-to-one user-to-host experience

### Use Cases:
- IT administration of servers or endpoints
- Remote work access to office machines
- Helpdesk troubleshooting

### Security Considerations:
- **Default port**: TCP 3389
- Frequently targeted by:
  - **Brute-force attacks**
  - **RDP hijacking**
  - **Man-in-the-Middle (MitM) attacks** if improperly secured
- **Mitigation strategies**:
  - Enforce **strong password policies**
  - Use **multi-factor authentication (MFA)**
  - Place behind **VPNs or Remote Desktop Gateways**
  - Employ **network-level authentication (NLA)**
  - Monitor with **SIEM** tools and endpoint detection systems

---

## Remote Desktop Gateway (RD Gateway)

Acts as a proxy between external RDP clients and internal RDP hosts. Benefits include:
- Single, secure point of entry
- Integration with **Active Directory**
- **HTTPS encapsulation** of RDP traffic
- Reduces the need to expose RDP ports directly to the Internet

---

## Alternatives to RDP

### 1. **TeamViewer**
- Cross-platform remote control and support
- Cloud-based and user-friendly
- Uses TLS + AES encryption
- Suited for helpdesk and non-technical users

### 2. **Virtual Network Computing (VNC)**
- Open standard remote desktop system using **RFB (Remote Frame Buffer) protocol**
- Many implementations (e.g., RealVNC, TightVNC, TigerVNC)
- Platform-independent

> Note: VNC lacks strong native encryption — should be used **with an SSH tunnel or VPN**.

### 3. **Clientless Remote Desktop (HTML5 VPN)**

- Remote desktop over a **web browser** using **HTML5 `<canvas>`** and **WebSocket**
- No dedicated client software needed
- Examples: **Apache Guacamole**
- Works across OS platforms
- **Secure, scalable**, and ideal for cloud access portals

---

## Protocol: WebSocket

- Enables **bidirectional communication** between browser and server
- Avoids the overhead of HTTP polling
- Used in modern remote access solutions for real-time performance (e.g., HTML5 RDP/VNC gateways)

---

## Deployment Models

| Model                | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| Direct RDP           | Client connects to exposed host over port 3389 (not recommended)            |
| VPN + RDP            | RDP only accessible after VPN tunnel is established                         |
| Remote Desktop Gateway | HTTPS-tunneled RDP traffic via RD Gateway (recommended enterprise setup)  |
| HTML5 Remote Desktop | Browser-based access using WebSockets and HTML5, often with Guacamole       |

---

## Security Best Practices

- **Never expose RDP directly to the Internet**
- Restrict by **IP address or VPN access**
- Implement **MFA** and **network-level authentication (NLA)**
- Use **strong encryption protocols**
- Regularly update and patch RDP services
- Monitor with **audit logs and SIEM tools**
- Use **TLS certificates** for RD Gateway services

---

## Related Topics

- [[VPNs and Tunneling Protocols]]
- [[TLS and WebSocket Security]]
- [[Apache Guacamole Overview]]
- [[Endpoint Security Monitoring]]
- [[Brute Force Attack Detection and Prevention]]

