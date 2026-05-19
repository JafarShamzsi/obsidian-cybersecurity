## 1. Introduction

The primary function of network infrastructure is to forward traffic between nodes. Each layer of the network consists of nodes (e.g., hosts, switches, routers) and links (e.g., cables, wireless connections) arranged in a topology that supports application workflows while optimizing for performance and security.

---
![[8730-1692974863226.png]]
## 2. Network Topology

A **topology** defines how nodes are interconnected. It can be:

- **Physical topology**: Actual layout of hardware and cabling.
- **Logical topology**: The path that data traverses through the network, regardless of physical arrangement.

Topologies are selected based on scalability, reliability, and security requirements.

---

## 3. On-Premises Networks

An **on-premises network** is deployed and managed at a single site by an organization. This setup is typically referred to as an enterprise LAN (Local Area Network). It offers direct control over hardware and policies and forms the basis for many internal IT infrastructures.

---
![[7407-1692974863353.png]]
## 4. Structured Cabling

### Components and Layout

Structured cabling is the standardized physical infrastructure used in office and campus networks. It typically includes:

- **Wall Ports**: Provide endpoint connectivity.
- **Patch Cables**: Connect end devices to wall ports and patch panels to switches.
- **Patch Panels**: Central distribution units where building-wide cabling terminates.
- **Switches**: Act as aggregation points for data forwarding.

### Cabling Path

1. A workstation connects to a wall port using a patch cable.
2. The wall port is wired to a patch panel via internal structured cabling.
3. A second patch cable connects the patch panel to a switch port.

This arrangement implements a **star topology**, where each host is connected to a central switch.

---

## 5. Broadcast Domains and Layer 2 Segments

In this setup, all devices connected to the same switch belong to the same **broadcast domain**:

- The switch forwards broadcast traffic to all connected hosts.
- Communication within the broadcast domain uses **MAC addressing**.
- This constitutes a **Layer 2 network segment**.

---

## 6. Limitations of Flat Network Topologies

Flat Layer 2 networks present several issues:

- **Performance Degradation**: Broadcast traffic increases linearly with the number of hosts.
- **Unrestricted Lateral Movement**: All hosts can initiate communications unless endpoint-level restrictions are enforced.
- **No Centralized Policy Enforcement**: Network devices (e.g., switches) do not prevent host-to-host traffic within the same segment.

From a cybersecurity perspective, flat networks increase the **attack surface** and facilitate **lateral movement** by threat actors.

---

## 7. Hierarchical Network Design

To mitigate the risks of flat networks, a **hierarchical design** is implemented using multiple layers:

### Access Layer

- Consists of **access switches** that connect endpoint devices such as:
  - Workstations
  - Printers
  - IP phones
  - IoT devices

Each access switch manages a group of hosts with similar trust profiles, forming an **access block**.

### Core Layer

- Comprises **routers** or **Layer 3 switches** that interconnect access blocks.
- Creates separate broadcast domains.
- Routes inter-block traffic using **IP addressing**.
- Enforces traffic control via ACLs, firewalls, or other Layer 3 policies.

This approach enables **zone-based security**: each block can have customized access controls depending on its role (e.g., guest devices vs internal workstations).

---

## 8. Layer 3 Switches

A **Layer 3 switch** combines routing and switching functions:

- Performs **Layer 2 switching** within VLANs.
- Handles **inter-VLAN routing**.
- Commonly used in the core or distribution layer of enterprise networks.
- Enables high-throughput routing and policy enforcement with lower latency than traditional routers.

---

## 9. Equipment Room and Secure Cabling

Enterprise-grade networking equipment is typically installed in a dedicated **equipment room**:

- Houses core switches, routers, servers, and network appliances.
- Restricted physical access ensures tamper resistance.
- **Servers** connect directly to switch ports using patch cables, bypassing wall ports.

---

## 10. Cybersecurity Considerations

Cybersecurity specialists must be aware of the following:

- **Segmentation**: Use VLANs and hierarchical design to enforce isolation and reduce attack surfaces.
- **Access Controls**: Deploy 802.1X authentication and MAC filtering at switch ports.
- **Monitoring**: Use traffic monitoring protocols (e.g., NetFlow, sFlow) for threat detection.
- **Least Privilege Access**: Enforce minimal communication pathways between segments.
- **Physical Security**: Ensure structured cabling and switch gear are inaccessible to unauthorized personnel.

---

## 11. Summary

Switching infrastructure is the foundation of enterprise connectivity. While a simple star topology suffices for small deployments, larger environments require hierarchical models to ensure performance, scalability, and security. Cybersecurity professionals must understand both the physical and logical architectures of switching infrastructure to enforce proper segmentation, detect threats, and reduce risk.

