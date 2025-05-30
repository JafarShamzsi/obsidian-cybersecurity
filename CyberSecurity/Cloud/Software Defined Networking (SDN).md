Software Defined Networking (SDN) is an architectural framework that separates the **control plane** from the **data plane** in networking devices, enabling programmable, centralized, and abstracted control over network behavior. SDN enables automation, rapid provisioning, and dynamic policy enforcement, which are critical in cloud-scale and hybrid environments.

SDN is foundational in cloud-native infrastructure, often implemented alongside **Infrastructure as Code (IaC)** and **Network Function Virtualization (NFV)**.

---

## SDN Architecture

### Key Planes of Operation

SDN abstracts and decouples network logic into three functional planes:

| Plane | Function |
|-------|----------|
| **Management Plane** | Monitors and reports network state. Provides analytics and status telemetry to admins and orchestration tools. |
| **Control Plane** | Makes policy decisions about routing, traffic prioritization, quality of service (QoS), and security enforcement. |
| **Data Plane** | Forwards packets based on instructions from the control plane. Implements firewall rules, ACLs, NAT, etc. |

This separation increases agility, simplifies policy management, and allows for more granular, dynamic control over network behaviour.
![[2672-1692974866728.png]]

---

### SDN Control Architecture

| Component | Description |
|-----------|-------------|
| **SDN Application Layer** | Defines intent and policy (e.g., routing, access control). Interfaces with the controller via **northbound APIs**. |
| **SDN Controller** | Central intelligence unit. Translates application-layer intent into network-level instructions. Interfaces with devices via **southbound APIs**. Examples: OpenDaylight, ONOS, Cisco APIC. |
| **Network Infrastructure Layer** | Includes physical and virtual routers, switches, firewalls, and load balancers. Receives control signals from the SDN controller. |

---

### API Layers

- **Northbound API**: Interface between SDN applications and controllers.
  - Example: RESTful API used to configure routing policies or QoS via an orchestration platform.
- **Southbound API**: Interface between controllers and physical/virtual network devices.
  - Examples: OpenFlow, NETCONF, gNMI, Cisco OpFlex.

---

## Network Functions Virtualization (NFV)

### Definition

NFV refers to the virtualization of network services (e.g., routing, firewalling, IDS/IPS, load balancing) that were traditionally run on proprietary, dedicated hardware appliances. These virtualized network functions (VNFs) run on general-purpose hardware using VMs or containers.

### Key Components

| Component | Description |
|-----------|-------------|
| **NFV Infrastructure (NFVI)** | Physical servers, storage, and network hardware hosting VNFs. |
| **VNF Manager (VNFM)** | Deploys, configures, and scales VNFs. |
| **NFV Orchestrator (NFVO)** | Coordinates the full lifecycle of NFV services across NFVI and VNFs. |
| **MANO (Management and Orchestration)** | ETSI-standardized framework managing NFV lifecycle. |

NFV is often used with SDN to deliver **virtualized, programmable networks** that are fully automated and scalable.

---

## Integration with IaC

### IaC and SDN Convergence

IaC tools (e.g., Terraform, Ansible) can be extended to provision and configure not just virtual machines and applications, but also **virtual networks and SDN policies**. SDN controllers expose APIs that IaC frameworks can invoke, allowing for:

- Automated provisioning of virtual routers, switches, and firewalls.
- Dynamic security policy injection (ACLs, microsegmentation).
- Real-time reconfiguration based on telemetry or deployment triggers.

This enables **Network as Code (NaC)**—treating network configurations like software artifacts.

---

## Use Cases

- **Data Center Fabric Automation**: Dynamically adjust routing paths and segment networks using VXLAN, EVPN.
- **Microsegmentation**: Enforce fine-grained east-west security controls between containers or VMs.
- **Zero Trust Networking**: Centralize identity-based access controls for traffic inside the perimeter.
- **Traffic Engineering**: Optimize bandwidth usage based on dynamic traffic flows.
- **Disaster Recovery and Multi-Region Failover**: Rebuild virtual networks automatically in alternate locations.

---

## Cybersecurity Implications

### Advantages

- **Centralized Policy Enforcement**: Single point of control for security policies across the fabric.
- **Dynamic Response**: Automatically reroute or quarantine malicious traffic based on threat intelligence or behavioral anomalies.
- **Improved Visibility**: Flow-level telemetry and full-packet captures across the data plane.

### Attack Surface and Risk Considerations

| Risk Vector | Description |
|-------------|-------------|
| **Controller Compromise** | Centralized nature of SDN introduces a single point of failure and control. Exploiting the controller can lead to full network compromise. |
| **API Exposure** | Unauthenticated or improperly authorized API calls (northbound or southbound) can result in unauthorized policy changes. |
| **Man-in-the-Middle (MitM)** | Insecure communication between controller and appliances (southbound) can be intercepted or modified. |
| **Configuration Drift** | If SDN policies are not integrated with IaC or version control, configuration inconsistencies may arise. |
| **Policy Misconfigurations** | Centralized policy push errors may affect thousands of endpoints simultaneously. Requires strong change validation processes. |

### Hardening Recommendations

- Implement **mutual TLS authentication** for all controller-API communications.
- Enforce **RBAC (Role-Based Access Control)** on all SDN components.
- Isolate the SDN control plane from the general-purpose data plane network.
- Use **code signing and validation** for policy templates and controller plugins.
- Integrate **SIEM and SOAR** platforms to monitor SDN telemetry and automate response.
- Employ **continuous security testing** of SDN policies and controller firmware (e.g., fuzzing, logic abuse, privilege escalation).

---

## Summary

Software Defined Networking revolutionizes how networks are architected, managed, and secured. By abstracting control and providing centralized programmability, SDN offers significant benefits in scalability, automation, and security orchestration. However, this power introduces new attack vectors that must be mitigated through robust identity control, encryption, rigorous change management, and active monitoring.

---

## Related Topics

- [[Infrastructure as Code (IaC)]]
- [[Zero Trust Architecture]]
- [[Network Segmentation and Microsegmentation]]
- [[Cloud Network Security Controls]]
- [[API Security Best Practices]]
- [[Container Networking and CNI Plugins]]
