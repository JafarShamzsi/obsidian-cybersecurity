## 1. Overview

Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) are critical network security technologies designed to detect, monitor, and respond to unauthorized, anomalous, or malicious network activity.

- **IDS (Intrusion Detection System)**: Passive system that monitors and analyzes traffic or logs to detect potential threats, generating alerts for further action.
    
- **IPS (Intrusion Prevention System)**: Active system that not only detects but also takes automated action to block or mitigate threats in real-time.
    

---
![[5840-1692974864918.png]]
## 2. Intrusion Detection Systems (IDS)

### 2.1. Purpose

- Provides **real-time analysis** of:
    
    - Network traffic (via packet capture)
        
    - System and application logs
        
- Main role is **detection and alerting**, not prevention.
    

### 2.2. Components

#### a. Sensors

- A **network IDS (NIDS)** sensor uses a **packet sniffer** to capture network traffic.
    
- Deployment locations:
    
    - Behind perimeter firewalls
        
    - Near high-value assets (e.g., critical servers)
        
- **Capture methods**:
    
    - **SPAN/mirror ports** (switch-level port replication)
        
    - **Inline TAPs** (Test Access Points)
        
- Sensors should be:
    
    - Strategically located
        
    - Limited in number based on resources
        
    - Properly managed to avoid blind spots
        

#### b. Data Collection and Analysis

- Traffic from sensors is sent to a host running IDS software.
    
- Common open-source IDS tools:
    
    - **Snort** (signature-based)
        
    - **Suricata** (multi-threaded; supports rulesets)
        
    - **Zeek/Bro** (behavioral/heuristics-based)
        

### 2.3. Detection Capabilities

- **Signature Matching**:
    
    - Compares packet content to known threat patterns.
        
- **Heuristic/Anomaly Detection**:
    
    - Identifies deviations from normal behavior.
        

#### Examples of Detectable Activities:

- Brute-force login attempts
    
- Port scans (e.g., SYN scan)
    
- Protocol violations
    
- Malware command and control (C2) activity
    
- Lateral movement and privilege escalation
    

### 2.4. Passive Nature

- IDS does **not interfere** with traffic.
    
- Ideal for **stealth monitoring** — attackers are unaware of its presence.
    
- Output includes:
    
    - Alerts
        
    - Logs
        
    - Event correlation (via SIEM systems like Kibana, ELK stack)
        

---

## 3. Intrusion Prevention Systems (IPS)

### 3.1. Purpose

- Enhances IDS capabilities with **active response mechanisms**.
    
- Positioned **inline** to actively intercept and respond to threats.
    

### 3.2. Detection Mechanisms

- Similar to IDS: signature-based, anomaly-based, protocol decoding
    
- Runs **deep packet inspection (DPI)** to analyze:
    
    - Application-layer protocols
        
    - Packet payloads
        

### 3.3. Response Actions

- **Blocking (Shunning)**:
    
    - Drop or reject packets from malicious source addresses.
        
- **Connection Reset**:
    
    - Sends TCP RST packets to terminate the session without blocking.
        
- **Redirection to Honeypots**:
    
    - Lure attackers into a **controlled environment** for analysis and intelligence gathering.
        

### 3.4. Deployment Methods

#### a. Inline Mode

- Acts like a firewall:
    
    - Positioned between internal and external networks.
        
    - Directly intercepts traffic.
        
- Immediate and automated responses.
    

#### b. Passive + Orchestrated Mode

- Uses **passive detection** like an IDS.
    
- Works with other systems via:
    
    - **Scripts**
        
    - **APIs**
        
    - **Firewall policy updates**
        

### 3.5. Integration Examples

- **Security Onion** platform integrates:
    
    - Snort/Suricata IDS
        
    - Kibana for log analysis
        
    - Automated correlation with threat intel feeds
        
- **Firewalls with IPS modules** (e.g., Palo Alto, Cisco Firepower)
    

---

## 4. Strategic Considerations

|IDS|IPS|
|---|---|
|Passive (alert only)|Active (can block)|
|Cannot stop attacks|Can prevent damage in real time|
|Stealthy and undetectable by attackers|Detectable and potentially a target|
|Easier to deploy with minimal disruption|Can introduce latency if not optimized|