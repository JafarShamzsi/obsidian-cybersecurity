Load balancers are critical components in distributed systems architecture. They improve availability, scalability, and fault tolerance by distributing incoming network traffic across multiple servers. This ensures no single server bears too much load and that services remain operational in the event of server failure.

---

## Core Functions

- **Traffic Distribution**: Routes incoming client requests to available servers in a load-balanced pool.
- **Scalability**: Allows services to scale horizontally by adding more nodes without altering client behavior.
- **Fault Tolerance**: Detects and isolates failed nodes, redirecting traffic to healthy servers.
- **DDoS Mitigation**: Helps absorb volumetric denial-of-service attacks by distributing load across multiple backends.
![[image-5fa9b59ddacd0.jpg]]
---

## Types of Load Balancers

### Layer 4 Load Balancer (Transport Layer)

- Makes decisions based on **IP addresses and TCP/UDP port numbers**.
- Does not inspect packet content beyond the transport layer.
- Fast and efficient for general-purpose load balancing.
- Suitable for applications where content-based routing is not needed.

### Layer 7 Load Balancer (Application Layer / Content Switch)

- Makes decisions based on **application-layer data** (e.g., HTTP headers, URL paths, MIME types).
- Supports **deep packet inspection** and content-aware routing (e.g., routing `/video` traffic to a media-optimized server).
- Capable of performing **SSL offloading**, **web application firewall (WAF)** integration, and **cookie-based session persistence**.
- More computationally intensive than Layer 4, but enables fine-grained traffic control.

---

## Basic Load Balancing Process

1. **Client Connection**: The client sends a request to a public-facing virtual IP managed by the load balancer.
2. **Backend Selection**: The load balancer evaluates its algorithm and health data to select a server instance.
3. **Traffic Forwarding**: The selected server handles the client’s request.
4. **Persistence**: If configured, the client remains bound to the selected server throughout the session.

---

## Scheduling Algorithms

The scheduling algorithm governs how backend servers are selected. Options include:

- **Round Robin**
  - Simple rotation among available servers.
  - Each server receives requests in a sequential, circular order.

- **Least Connections**
  - Assigns traffic to the server with the fewest active connections.
  - Useful in cases where client session durations vary.

- **Least Response Time**
  - Selects the server that responds quickest to health probes or test queries.

- **Weighted Algorithms**
  - Uses administrator-assigned or dynamic weights to influence selection.
  - Allows for node prioritization based on capacity or hardware performance.

---

## Health Checks and Availability Probes

To avoid routing traffic to unavailable nodes, load balancers implement health checks:

- **Layer 4 Probes**
  - Basic TCP/UDP connectivity tests.
  - Detects if the host responds on the expected port.

- **Layer 7 Probes**
  - Application-specific checks (e.g., HTTP GET `/status` endpoint).
  - Can evaluate business logic (e.g., verify app is not in maintenance mode).

---

## Session Persistence Mechanisms

Session persistence ensures clients remain connected to the same backend during an active session. This is critical for applications with stateful user interactions.

### Source IP Affinity (Layer 4)

- Binds a client to a specific backend using the client's IP address.
- Simpler but can be unreliable if the client is behind a NAT or proxy pool.

### Cookie-Based Persistence (Layer 7)

- Inserts a session identifier in the form of a **cookie**.
- Requires that the client supports and accepts cookies.
- Offers more granular and resilient tracking of sessions, especially in web environments.

---

## Use Cases

- **Web and Application Servers**
- **Streaming Media Services**
- **Front-End Email Gateways**
- **VoIP and Video Conferencing Platforms**
- **Reverse Proxy and SSL Offloading**

---

## Security Implications

- **Load balancers must be hardened** as they are exposed entry points into a network.
- **Session persistence methods** must avoid leaking user data or creating security holes (e.g., improperly secured cookies).
- In **cloud environments**, load balancers integrate with auto-scaling groups and often include **Web Application Firewall (WAF)** and **DDoS protection** features.

---

## Related Topics

- [[Reverse Proxy and Forward Proxy]]
- [[TLS Offloading and SSL Termination]]
- [[High Availability and Failover Design]]
- [[Web Application Firewall (WAF)]]
- [[Zero Trust Network Design]]

