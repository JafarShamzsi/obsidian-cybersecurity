## Layer 3 Forwarding and Logical Addressing

Layer 3 forwarding, or routing, is the process by which packets are moved between different broadcast domains using logical addressing. Internet Protocol (IP) is the fundamental Layer 3 protocol used to assign unique logical addresses to each node in a network. Each Layer 3 segment, or subnet, forms a distinct broadcast domain and typically aligns with a specific organizational or functional boundary within the network.

Routing infrastructure enables segmentation of enterprise networks into subnets, allowing for granular control over traffic flow, policy enforcement, and fault isolation. These subnets are defined by IP address ranges and subnet masks or prefix lengths. Routing decisions are made based on destination IP addresses using routing tables, which may include both static and dynamically learned routes (via routing protocols such as OSPF, EIGRP, or BGP).

## IPv4 Addressing

IPv4 uses a 32-bit addressing scheme typically represented in dotted decimal notation (e.g., `10.1.1.0`). IP addressing is logically divided into two parts:

- **Network ID**: Defines the subnet or logical network.
    
- **Host ID**: Identifies a unique device within the subnet.
    

A CIDR (Classless Inter-Domain Routing) notation is used to define the subnet mask. For example:

```
IP Address: 10.1.1.0/24
Subnet Mask: 255.255.255.0
```

In this example, `/24` indicates that the first 24 bits represent the network portion, leaving 8 bits for host addressing within the subnet. This provides 256 total IP addresses (254 usable for hosts).
![[6565-1692974863528.png]]
## IPv6 Addressing

IPv6 provides a 128-bit addressing model, supporting a vastly larger address space than IPv4. Addresses are expressed in hexadecimal notation, typically separated by colons, such as:

```
2001:db8::abc:0:def0:1234
```

IPv6 addressing is hierarchical:

- The **first 64 bits** represent the network prefix (including global routing prefix and subnet ID).
    
- The **last 64 bits** represent the interface identifier (typically derived from the MAC address or randomly generated).
    

IPv6 replaces ARP with Neighbor Discovery Protocol (NDP) for MAC address resolution and network discovery functions.
![[8218-1692974863714.png]]
## Address Resolution

At the link layer, IP addresses must be resolved to MAC addresses to enable Layer 2 frame delivery:

- **IPv4** uses the Address Resolution Protocol (ARP) to map IP addresses to MAC addresses.
    
- **IPv6** uses the Neighbor Discovery Protocol (NDP) for similar functionality.
    

This resolution is necessary because routers make forwarding decisions based on IP addresses but rely on MAC addresses for actual delivery within the local network segment.

## Routing Hierarchy and Network Segmentation

A hierarchical enterprise network architecture divides the infrastructure into functional layers and logical subnets:

- **Access Layer**: Connects end devices such as printers, workstations, IP phones, and servers. Each group of devices is typically assigned a dedicated subnet.
    
- **Distribution Layer**: Aggregates access layer switches and performs routing between VLANs and subnets.
    
- **Core Layer**: Provides high-speed backbone connectivity and interconnects distribution layers or data centers.
    

### Example Topology

- The access layer connects three distinct subnets:
    
    - `10.1.48.0/24` (printers)
        
    - `10.1.32.0/24` (workstations and VoIP)
        
    - `10.1.16.0/24` (private application and database servers)
        
- These are routed via a Layer 3 switch or router to a border router/firewall through a transit subnet, e.g., `10.1.128.0/24`.
    
- A separate network (e.g., `192.168.42.0/24`) services a Wi-Fi access point for guest connectivity, which is logically and physically segmented from the enterprise LAN.
    

## Virtual LANs (VLANs)

VLANs provide Layer 2 segmentation within switched networks, enabling separation of traffic without requiring physical isolation. VLANs are identified by unique VLAN IDs (ranging from 1 to 4094, excluding reserved IDs).

Each VLAN operates as a distinct broadcast domain. Switch ports are configured as either:

- **Access ports**: Assigned to a single VLAN.
    
- **Trunk ports**: Carry traffic for multiple VLANs using IEEE 802.1Q tagging.
    

### Inter-VLAN Routing

Traffic between VLANs must traverse a Layer 3 device (e.g., a router or multilayer switch). Each VLAN is typically associated with a dedicated subnet. A Layer 3 interface, often a switched virtual interface (SVI), is configured for each VLAN to facilitate routing.

**Example Configuration:**

- VLAN 32: Workstations, Subnet `10.1.32.0/24`
    
- VLAN 40: VoIP handsets, Subnet `10.1.40.0/24`
    

Although devices in both VLANs might connect to the same physical switch, they are logically isolated. Communication between them requires routing, and access control lists (ACLs) or firewall rules can be applied to restrict or permit specific traffic types.

## VLAN Extension and Scalability

VLANs can span multiple switches using trunk links, allowing consistent segmentation across multiple physical locations. For example, when a business expands to multiple floors or buildings, the same VLANs can be configured across all switches, maintaining uniform segmentation policies.

This model supports scalable and flexible design patterns such as:

- **End-to-End VLANs**: Same VLANs span entire networks, simplifying device mobility.
    
- **Local VLANs**: VLANs are localized to specific areas, reducing broadcast traffic and enhancing manageability.