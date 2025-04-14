## **1. MITRE ATT&CK Framework**

🔹 **What it is**: A globally accessible knowledge base that documents **tactics, techniques, and procedures (TTPs)** used by cyber adversaries.  
🔹 **Who uses it**: Security analysts, threat hunters, and incident responders.  
🔹 **Why it's important**: Helps organizations **detect, prevent, and respond** to attacks by mapping adversary behavior.

### **Structure of MITRE ATT&CK**

- **Tactics**: The _why_ behind an attack (e.g., Initial Access, Privilege Escalation).
- **Techniques**: The _how_ of an attack (e.g., Spear-phishing, DLL Injection).
- **Procedures**: The specific _implementation_ of a technique by a threat actor.

### **Example Tactic-Technique Pairing**

|**Tactic**|**Technique**|**Example APT Group**|
|---|---|---|
|Initial Access|Spear-phishing (T1566)|APT29 (Cozy Bear)|
|Privilege Escalation|Token Impersonation (T1134)|APT28 (Fancy Bear)|
|Defense Evasion|Rootkit Installation (T1014)|Lazarus Group (North Korea)|
|Credential Access|Mimikatz (T1003)|APT10 (China)|

🔹 **How to use it**:

1. **Map attack behavior** to MITRE ATT&CK techniques.
2. **Identify gaps** in security defenses.
3. **Simulate attacks** using frameworks like **Atomic Red Team** or **Caldera**.

🛠️ **Tools for MITRE ATT&CK**:

- MITRE ATT&CK Navigator
- [CALDERA (Automated Adversary Emulation)](https://github.com/mitre/caldera)
- [Atomic Red Team (Testing ATT&CK techniques)](https://github.com/redcanaryco/atomic-red-team)

---

## **2. Lockheed Martin Cyber Kill Chain**

🔹 **What it is**: A **military-inspired** framework that describes **the 7 stages of a cyberattack** from initial reconnaissance to data exfiltration.  
🔹 **Why it's useful**: Helps security teams **detect and disrupt** attacks at various stages.

### **Cyber Kill Chain Stages**

|**Stage**|**Description**|
|---|---|
|**1. Reconnaissance**|Attackers gather intel (e.g., OSINT, network scanning).|
|**2. Weaponization**|Creating malware or exploits to attack the target.|
|**3. Delivery**|Sending the exploit (e.g., phishing, watering hole attacks).|
|**4. Exploitation**|Gaining initial access by executing the payload.|
|**5. Installation**|Establishing persistence (e.g., backdoors, rootkits).|
|**6. Command & Control (C2)**|Remote access to compromised systems.|
|**7. Actions on Objectives**|Final goal (e.g., data theft, ransomware deployment).|

🔹 **How to use it**:

- Identify which stage an attack is in and apply **mitigation strategies** (e.g., detecting phishing in the **delivery stage**).
- Map threats from **Cyber Kill Chain** to **MITRE ATT&CK** for better defense.

---

## **3. Diamond Model of Intrusion Analysis**

🔹 **What it is**: A **visual framework** used to understand how attacks occur by breaking them into four key elements:

1. **Adversary** – The attacker (e.g., APT29).
2. **Capability** – The tools they use (e.g., Cobalt Strike, Mimikatz).
3. **Infrastructure** – How they launch attacks (e.g., C2 servers, phishing domains).
4. **Victim** – The target (e.g., a financial institution).

🔹 **Why it's useful**:

- Helps **track attack patterns** across multiple incidents.
- Connects different aspects of an attack (e.g., if the same **infrastructure** is used, another attack might be coming).

---

## **4. Unified Kill Chain**

🔹 **What it is**: A **modern extension** of the Cyber Kill Chain that merges it with **MITRE ATT&CK** and **real-world attack strategies**.  
🔹 **Why it's better than Cyber Kill Chain**:

- Accounts for **lateral movement** inside a network.
- Covers **multi-phase** and **multi-vector** attacks.
- Improves tracking of **persistent** threats like APTs.

### **Unified Kill Chain Stages**

|**Stage**|**Description**|
|---|---|
|Initial Foothold|Gaining entry (e.g., phishing, watering hole attack).|
|Network Propagation|Lateral movement inside the network.|
|Asset Manipulation|Exfiltrating, encrypting, or corrupting data.|

🛠️ **Recommended Tool**:

- **[Unified Kill Chain framework](https://unifiedkillchain.com/)** (for deeper attack analysis).

---

## **5. STRIDE Threat Model**

🔹 **What it is**: A **Microsoft-developed framework** for classifying security threats.  
🔹 **Why it's useful**: Helps security teams **analyze vulnerabilities** in applications and systems.

### **STRIDE Categories**

|**Threat**|**Example Attack**|
|---|---|
|**Spoofing**|Identity theft (e.g., stolen credentials).|
|**Tampering**|Data manipulation (e.g., modifying financial records).|
|**Repudiation**|Denying actions (e.g., deleting logs).|
|**Information Disclosure**|Data leaks (e.g., sensitive info in logs).|
|**Denial of Service (DoS)**|Service disruption (e.g., DDoS attack).|
|**Elevation of Privilege**|Gaining unauthorized access (e.g., privilege escalation).|

🛠️ **Recommended Tool**:

- **Microsoft Threat Modeling Tool** (to apply STRIDE in security assessments).

---

## **Which Attack Framework Should You Use?**

|**Framework**|**Best For**|
|---|---|
|**MITRE ATT&CK**|Tracking **nation-state actors** and **APTs**.|
|**Cyber Kill Chain**|Understanding the **stages** of an attack.|
|**Diamond Model**|**Visualizing** attack patterns and attribution.|
|**Unified Kill Chain**|**Detecting advanced threats** that move laterally.|
|**STRIDE**|**Threat modeling** for application security.|
