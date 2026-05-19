Account restrictions are **policy-enforced security mechanisms** that govern when, where, and how user accounts may authenticate or operate within an enterprise environment. These restrictions reduce the **attack surface** and help mitigate risks from compromised credentials or insider threats.

---

### Location-Based Restrictions

#### 1. **Logical Network Location**

- Defined via:
    
    - **IP Address**: e.g., `192.168.10.15`
        
    - **Subnet**: e.g., `192.168.10.0/24`
        
    - **Virtual LAN (VLAN)**: e.g., VLAN ID 20 for the Finance Department
        
    - **Organizational Unit (OU)**: e.g., `OU=Servers,DC=corp,DC=example,DC=com`
        
- **Use Case**: Restrict local logon to specific systems based on OU or VLAN assignment.
    
- **Implementation**:
    
    - GPO > `Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment > Deny log on locally`
        
    - Conditional Access in Azure AD with Named Locations
        

#### 2. **Geolocation-Based Enforcement**

##### a. **IP-Based Geolocation**

- Approximate mapping of public IP addresses to:
    
    - Country
        
    - Region/State
        
    - City
        
- **Tools**:
    
    - MaxMind’s GeoIP2
        
    - IP2Location
        
- **Limitations**:
    
    - Accuracy varies by ISP
        
    - VPN/proxy usage may obfuscate actual location
        

##### b. **Location Services (Device-Based)**

- **GPS Sensors**:
    
    - High accuracy outdoors
        
    - Accessed through OS APIs (e.g., `Windows.Devices.Geolocation`)
        
- **Network-Based Location**:
    
    - Uses triangulation via:
        
        - Cell towers
            
        - Wi-Fi access points
            
        - Bluetooth beacons
            
- **Platforms**:
    
    - Windows Location API
        
    - Mobile Device Management (MDM) platforms (e.g., Intune, Jamf)
        

---

### Time-Based Restrictions

Time-based access control helps mitigate **after-hours attacks**, **lateral movement**, and **credential misuse** across different geotemporal contexts.

#### 1. **Time-of-Day Restrictions**

- **Definition**: Specify allowable hours for user authentication.
    
- **Implementation**:
    
    - In **Active Directory Users and Computers (ADUC)**:
        
        - User Object → Properties → Account → "Logon Hours"
            
    - In **Linux PAM** (e.g., `/etc/security/time.conf`)
        
- **Use Case**: Block non-business-hour logins for non-administrative users.
    

#### 2. **Duration-Based Login Policies**

- **Definition**: Set a maximum allowed session length.
    
- **Example**: Limit session time to 4 hours per login.
    
- **Implementation**:
    
    - Windows: Group Policy → `Interactive logon: Machine inactivity limit`
        
    - Linux: `TMOUT` environment variable or shell wrappers in `/etc/profile.d`
        

#### 3. **Impossible Travel Detection / Risky Logins**

- **Concept**: Track user login events across locations and timestamps.
    
- **Logic**:
    
    - If a login from Location A at time `t1` is followed by login from Location B at `t2`, calculate travel time.
        
    - If `t2 - t1` < minimum plausible travel duration → mark as **impossible travel**
        
- **Security Response**:
    
    - Alert raised
        
    - Session terminated
        
    - Account temporarily disabled or locked
        
- **Implementation**:
    
    - Azure AD Identity Protection
        
    - SIEM rules (e.g., Sentinel, Splunk, ELK with GeoIP enrichment)
        
    - Microsoft 365 Defender or third-party IAM tools (e.g., Okta, PingIdentity)
        

#### 4. **Temporary Permissions Policy**

- **Purpose**: Automatically revoke elevated access or group membership after a defined interval.
    
- **Use Cases**:
    
    - Contractor access
        
    - Emergency “break glass” accounts
        
    - Just-In-Time (JIT) privilege assignment
        
- **Implementation**:
    
    - Azure Privileged Identity Management (PIM)
        
    - Scripts via PowerShell + `Remove-ADGroupMember` + scheduled task
        
    - GPO/LDAP policies integrated with expiration tags (e.g., `memberTimeToLive` in dynamic groups)
        

---

### Security Benefits

- Reduces **exposure window** for credential misuse.
    
- Prevents **lateral movement** from unexpected geographic or temporal locations.
    
- Enables **adaptive security posture** based on contextual signals (e.g., risk level, location, time).
    
- Enhances **compliance** with access governance frameworks (e.g., ISO/IEC 27001, NIST 800-53 AC-10, AC-17).
    

---

### Best Practices

- Implement **multi-layered restrictions**: combine location + time + device posture.
    
- Monitor for **VPN misuse** and **location spoofing** via logs and heuristics.
    
- Maintain **audit trails** for all restricted access denials and policy changes.
    
- Use **automated rule engines** for role expiration and geo-anomaly detection.
    
- Perform **periodic reviews** of logon time and group membership restrictions.
    

---

### Related References

- **Microsoft Docs** – [Set Logon Hours for AD Users](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/logon-hours)
    
- **NIST SP 800-53 Rev. 5**:
    
    - AC-10: Concurrent Session Control
        
    - AC-17: Remote Access
        
    - AC-20: Use of External Systems
        
- **CIS Controls v8**:
    
    - Control 6.7: Use Time-Based Access