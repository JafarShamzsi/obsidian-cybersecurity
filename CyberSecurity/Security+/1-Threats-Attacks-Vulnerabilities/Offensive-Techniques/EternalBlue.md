## Overview

EternalBlue is a critical SMB vulnerability (MS17-010) that was leaked by the Shadow Brokers group in April 2017 and was notably used in the WannaCry ransomware attack in May 2017. It exploits a vulnerability in Microsoft's Server Message Block (SMB) protocol, specifically SMBv1.

## Technical Details

### Vulnerability Analysis

- **CVE**: CVE-2017-0144
- **Affected Systems**: Windows XP, Windows 7, Windows Server 2003, Windows Server 2008, Windows Server 2008 R2, Windows Vista, Windows 8.1, Windows 10, Windows Server 2012, and Windows Server 2016 (before patches)
- **Protocol**: SMB v1 (TCP port 445)
- **Exploit Type**: Remote Code Execution (RCE)

### Exploitation Mechanics

EternalBlue exploits a buffer overflow vulnerability in the SMBv1 protocol. The vulnerability exists in how the SMB server handles specially crafted packets. When exploited, it allows attackers to execute arbitrary code with SYSTEM privileges without authentication.

The exploit works by:

1. Crafting malformed SMB packets that trigger buffer overflows
2. Overwriting memory with shellcode
3. Gaining SYSTEM-level execution privileges
4. Establishing persistence or delivering payload (often ransomware)

## Detection Methods

### Network Traffic Indicators

- Abnormal SMB traffic on port 445
- Unusual patterns of failed authentication attempts
- Large amounts of outbound traffic from SMB servers
- Suspicious communication with known C2 servers

### SIEM Detection Rules

```
# Suricata/Snort Rule Example
alert tcp $EXTERNAL_NET any -> $HOME_NET 445 (msg:"ETERNALBLUE MS17-010 SMB RCE Attempt"; flow:to_server,established; content:"|FF|SMB|73|"; offset:4; depth:5; content:"|00 00 00 00 00 00 00 00 00 00 00 00|"; distance:28; within:12; pcre:"/\x00\x31\x00|\x00\x32\x00|\x00\x33\x00/"; flowbits:set,smb.trans2; flowbits:noalert; sid:1000001; rev:1;)
```

### Host-based Detection

- Windows Event Log entries:
    
    - Event ID 4625: Failed logon attempts
    - Event ID 7045/4697: Service installation
    - Event ID 5156: Windows Filtering Platform connection blocked
- PowerShell detection script:
    

```powershell
# Check if system is patched for MS17-010
$hotfix = Get-HotFix -Id KB4012212, KB4012213, KB4012214, KB4012215, KB4012216, KB4012217, KB4012598, KB4013429, KB4013389
if (!$hotfix) {
    Write-Host "VULNERABLE: System missing MS17-010 patch" -ForegroundColor Red
} else {
    Write-Host "PATCHED: System has MS17-010 patch installed" -ForegroundColor Green
}

# Check if SMBv1 is enabled (potentially vulnerable)
$smbv1 = Get-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
if ($smbv1.State -eq "Enabled") {
    Write-Host "WARNING: SMBv1 is enabled" -ForegroundColor Yellow
} else {
    Write-Host "SECURE: SMBv1 is disabled" -ForegroundColor Green
}
```

## Technical Walkthrough (Understanding Context)

For educational purposes, here's how the exploit typically works in technical terms:

1. **Reconnaissance**:
    
    - Identify vulnerable Windows systems with open port 445
    - Confirm SMBv1 protocol is enabled
    - Verify system is unpatched for MS17-010
2. **Initial Connection**:
    
    - Establish SMB session with target
    - Send SMB negotiation packets to determine protocol version
3. **Exploitation**:
    
    - Send specially crafted Trans2 SMB packets that trigger buffer overflow
    - Use specific offsets to overwrite memory locations with shellcode
    - Execute initial shellcode to gain SYSTEM privileges
4. **Post-Exploitation**:
    
    - Install backdoor or deliver payload (DoublePulsar was often used)
    - Establish persistence
    - Move laterally through network using SMB credentials

## Mitigation Strategies

1. **Patch Management**:
    
    - Apply MS17-010 security update (released March 14, 2017)
    - Keep systems updated with latest security patches
2. **Protocol Hardening**:
    
    - Disable SMBv1:
        
        ```powershell
  # PowerShell command to disable SMBv1Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
        ```
        
    - Use SMBv3 with encryption where possible
3. **Network Segmentation**:
    
    - Block SMB ports (139, 445) at network boundaries
    - Implement proper network segmentation to limit lateral movement
4. **Monitoring**:
    
    - Deploy IDS/IPS with updated signatures
    - Monitor for unusual SMB traffic patterns
    - Configure Windows Event Log auditing for SMB events

## Related Exploits

- **DoublePulsar**: A backdoor implant often deployed by EternalBlue
- **EternalRomance**: Another SMB exploit from the Shadow Brokers leak
- **WannaCry**: Ransomware that leveraged EternalBlue for propagation
- **NotPetya**: Destructive malware that used EternalBlue among other techniques

## More execution methods
- https://gist.github.com/infosecn1nja/a3b703e025525e860000c7473490193f
- https://blog.stealthsecurity.sh/how-to-exploit-the-eternalblue-vulnerability-on-windows-a-step-by-step-guide-0d9d90b6397c
- https://blu3ming.github.io/windows-7-eternalblue/# (to create in lab)

## References

1. Microsoft Security Bulletin MS17-010: https://docs.microsoft.com/en-us/security-updates/securitybulletins/2017/ms17-010
2. CVE-2017-0144: https://nvd.nist.gov/vuln/detail/CVE-2017-0144
3. MITRE ATT&CK - EternalBlue: https://attack.mitre.org/techniques/T1210/
4. US-CERT Alert (TA17-132A): https://www.cisa.gov/news-events/alerts/2017/05/12/indicators-compromise-wannacrypt-ransomware

## Tags

#security #vulnerability #exploit #SMB #MS17-010 #EternalBlue #windows #ransomware