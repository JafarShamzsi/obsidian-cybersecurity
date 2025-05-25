Port security is a critical element of network access control, designed to prevent unauthorized devices from physically or logically connecting to enterprise networks. Unsecured switch and wall ports present potential entry points for attackers with physical access, who may exploit them to gain internal access or launch local network-based attacks.

---

## Physical Port Security

### Physical Protection of Switches

- **Secure Placement**: Network switches must be placed in physically secured environments (e.g., server rooms, locked cabinets).
    
- **Access Restriction**: Only authorized personnel should have physical access to networking hardware.
    

### Wall Port Control

- **Disable Unused Ports**: Administratively disable ports that are not actively in use via switch configuration.
    
- **Cable Management**: Physically disconnect patch cables from unused switch ports to mitigate risk.
    

> ⚠️ These methods are static and high-maintenance. An attacker can unplug a legitimate device from an enabled port and plug in their own machine.

---

## MAC Filtering and Limiting

### MAC Filtering

- Limits traffic on a specific switch port to devices with pre-approved MAC addresses.
    
- Static or dynamic MAC address assignment:
    
    - **Static**: Administrator specifies allowed MACs.
        
    - **Dynamic**: First N learned MAC addresses are permitted (common for VoIP + desktop dual connections).
        

### MAC Limiting

- Restricts the number of MAC addresses allowed on a given port.
    
- Example: A port may be configured to allow only two MAC addresses. Any additional MACs are dropped.
    
![[7891-1692974864032.png]]
#### Limitations

- **MAC Spoofing**: Adversaries can easily spoof legitimate MAC addresses.
    
- **Administrative Overhead**: Static assignment and manual oversight create complexity in large environments.
    

---

## IEEE 802.1X: Port-Based Network Access Control

802.1X is a robust framework for **authenticated network access**, overcoming the limitations of MAC-based security by enforcing identity-based access control.

### Key Components

|Component|Description|
|---|---|
|**Supplicant**|Endpoint device (e.g., PC, laptop) requesting access to the network.|
|**Authenticator**|Network device (e.g., switch, WAP) acting as gatekeeper. Forwards credentials to RADIUS.|
|**Authentication Server**|Validates the supplicant using credentials stored in a directory service (e.g., AD).|

### Protocol Stack

- **EAP (Extensible Authentication Protocol)**: Framework supporting multiple authentication types (e.g., certificates, smart cards).
    
- **EAPoL (EAP over LAN)**: Transports EAP messages between supplicant and authenticator.
    
- **RADIUS**: Facilitates communication between the authenticator and authentication server.
    

---

## 802.1X Authentication Flow
```
sequenceDiagram
    participant Supplicant
    participant Switch (Authenticator)
    participant RADIUS Server (Auth Server)

    Supplicant->>Switch: Connects to switch port
    Switch->>Supplicant: EAPoL - Request Identity
    Supplicant->>Switch: EAPoL - Response (identity)
    Switch->>RADIUS Server: RADIUS Access-Request (with EAP)
    RADIUS Server-->>Switch: Access-Challenge / Access-Accept
    Switch->>Supplicant: EAPoL - Success
    Switch->>Supplicant: Enables full network access

```

### Detailed Steps

1. **Connection Initiation**:
    
    - Supplicant connects to the switch port.
        
2. **EAP Negotiation**:
    
    - Switch enables EAPoL and prompts supplicant for credentials.
        
3. **Credential Forwarding**:
    
    - Credentials are encapsulated in EAP and forwarded to RADIUS server.
        
4. **Authentication Decision**:
    
    - RADIUS validates credentials against a backend directory (e.g., Active Directory).
        
5. **Access Granting**:
    
    - On success, RADIUS sends an Access-Accept message.
        
    - Switch opens the port for normal traffic.
        

---

## Benefits of 802.1X

- **Identity-Based Access Control**: Ties access to authenticated user or device identity.
    
- **Extensibility**: Supports multiple EAP types (TLS, TTLS, PEAP, MS-CHAPv2).
    
- **Dynamic VLAN Assignment**: Users can be placed into different VLANs based on authorization level.
    
- **Accounting Integration**: Through RADIUS, logs authentication events for auditing.
    

---

## Threats and Mitigations

|Threat|Mitigation|
|---|---|
|MAC Spoofing|Use 802.1X with certificate-based EAP|
|Physical Plug-In Attacks|Lock hardware cabinets, disable unused ports|
|Port Hopping or Rogue Devices|Enable dynamic ARP inspection, port security policies|
|Insecure Authentication Methods|Prefer EAP-TLS or EAP-TTLS with mutual authentication|
