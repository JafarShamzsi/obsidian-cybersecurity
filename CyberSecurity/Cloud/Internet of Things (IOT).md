The **Internet of Things (IoT)** refers to the network of interconnected physical objects—devices, sensors, appliances, vehicles—embedded with software, sensors, and connectivity to collect, exchange, and act upon data. These devices interact with each other and external systems, often via cloud-based platforms, to enable real-time automation, monitoring, and control.

IoT architectures typically involve:
- **Sensors**: Detect physical changes (temperature, motion, humidity, etc.).
- **Actuators**: Perform actions based on sensor data (e.g., turn on lights, unlock doors).
- **Connectivity**: Wi-Fi, Zigbee, BLE, NB-IoT, LoRaWAN, 5G.
- **Edge Processing Units**: Perform local decision-making.
- **Cloud Infrastructure**: Handle large-scale data analytics, device management, and orchestration.

---

## Use Cases and Applications

### Smart Homes
- Lighting, HVAC, and security automation
- Remote access via mobile applications
- Integration with digital assistants (e.g., Alexa, Google Assistant)

### Smart Cities
- Traffic optimization and vehicle tracking
- Environmental monitoring (air quality, noise, pollution)
- Public safety and surveillance systems

### Healthcare
- Wearable devices for heart rate, blood pressure, glucose monitoring
- Remote patient monitoring and telehealth systems
- Implantable IoT (e.g., pacemakers with telemetry)

### Industrial IoT (IIoT) & Agriculture
- SCADA integration for machinery and control systems
- Soil and irrigation monitoring
- Predictive maintenance through sensor analytics

---

## Drivers of IoT Adoption

- **Decreased Hardware Costs**: Sensor and microcontroller prices have dropped significantly.
- **Advancements in Wireless Connectivity**: Introduction of 5G, LPWAN, and mesh networking.
- **Edge and Cloud Computing**: Increased computational capacity for real-time analytics.
- **Machine Learning and AI**: Enabling predictive insights from sensor data.
- **Pandemic-Driven Remote Monitoring**: Accelerated use in healthcare and logistics during COVID-19.

---

## Security Risks Associated with IoT

### 1. Insecure Device Architecture
- Devices often ship with **default credentials**, open ports, and weak firmware.
- Limited memory and CPU resources restrict robust encryption and logging mechanisms.

### 2. Lack of Standardization
- Diverse protocols (MQTT, CoAP, proprietary stacks) create interoperability gaps.
- Varying security models among vendors complicate unified risk management.

### 3. Data Privacy Concerns
- Continuous data collection increases the attack surface for sensitive personal and operational data.
- Weak data-at-rest and data-in-transit protections lead to potential breaches.

### 4. Supply Chain Insecurity
- Components sourced from third-party vendors may contain backdoors or vulnerabilities.
- Firmware and software supply chains are rarely audited.

### 5. Cloud Dependency
- Cloud APIs may be misconfigured or lack adequate authentication controls.
- IoT platforms can become single points of failure.

---

## Notable Incidents

- **Mirai Botnet (2016)**:
  - Infected poorly secured IoT devices.
  - Launched record-breaking DDoS attacks via devices such as cameras and routers.

- **Casino Fish Tank Thermometer Breach**:
  - Smart thermometer exploited to pivot into the internal network.
  - Exfiltrated high-value data through an unsecured device.

- **Home Device Hijacks**:
  - Baby monitors and smart security cams accessed due to default passwords or vulnerable firmware.

---

## Root Causes of IoT Insecurity

- Focus on **functionality and time-to-market** over secure engineering.
- **Cost constraints** limiting investment in secure design and testing.
- **Rushed development cycles** and lack of independent security validation.
- **User ignorance** about security hygiene (e.g., unchanged passwords, outdated firmware).
- **Limited device update mechanisms**, resulting in persistent legacy vulnerabilities.

---

## Security Best Practices Checklist

### Device Hardening
- Change all default credentials.
- Disable unused ports/services.
- Disable JTAG, UART, and debug interfaces in production.
- Enforce secure boot and firmware validation.

### Network Security
- Segment IoT traffic using VLANs or firewalled subnets.
- Use zero trust principles for network access control.
- Restrict device internet access to only necessary endpoints.
- Use IDS/IPS systems to detect anomalous behavior.

### Communication Security
- Enforce TLS 1.2+ for all traffic.
- Use mutual authentication (device and server certificates).
- Encrypt sensitive payloads even on internal networks.

### Data Protection
- Encrypt data at rest using AES-256 or equivalent.
- Avoid storing sensitive data locally on devices unless necessary.
- Implement secure key storage (e.g., TPM, Secure Enclave).

### Update and Patch Management
- Provide secure OTA update mechanisms with digital signature validation.
- Track firmware versions and apply patches promptly.
- Audit update delivery channels for man-in-the-middle risks.

### Identity and Access Management
- Enforce least privilege with RBAC/ABAC models.
- Use MFA where applicable.
- Maintain unique identities and credentials per device.

### Logging and Monitoring
- Enable local and centralized logging (syslog, MQTT logging agents).
- Correlate with SIEM platforms for anomaly detection.
- Alert on abnormal communication patterns or access attempts.

---

## Industry Security Frameworks and Guidance

- **IoTSF (Internet of Things Security Foundation)**  
  https://iotsecurityfoundation.org

- **Industrial Internet Consortium (IIC) Security Framework**  
  https://www.iiconsortium.org/iisf/

- **Cloud Security Alliance IoT Controls Framework**  
  https://cloudsecurityalliance.org/artifacts/iot-security-controls-framework

- **ETSI EN 303 645 (Consumer IoT Security Standard)**  
  https://www.etsi.org/technologies/consumer-iot-security

---

## Recommendations

- Build security into the **device lifecycle** (design → deployment → decommissioning).
- Regularly audit **firmware, cloud APIs, and communication channels**.
- Educate users and IT teams about **configuration and patch hygiene**.
- Adopt and comply with internationally recognized **IoT cybersecurity standards**.
- Implement **zero trust architecture** for IoT integration into enterprise networks.

---

## Related Topics
- [[Zero Trust Architecture]]
- [[ICS/SCADA Security]]
- [[Firmware Analysis]]
- [[Threat Modeling]]
- [[Edge Computing Security]]

