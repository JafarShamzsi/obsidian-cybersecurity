## Overview

Simple Network Management Protocol (SNMP) enumeration tools allow security professionals and network administrators to discover, monitor, and extract information from network devices through SNMP. These tools can be used to identify device types, configurations, network structure, and potential security vulnerabilities.

## Popular SNMP Enumeration Tools

### 1. SNMPwalk

#### Overview

SNMPwalk is a command-line utility that uses SNMP GETNEXT requests to query a network entity for a tree of information. Part of the Net-SNMP suite, it's one of the most commonly used tools for SNMP enumeration.

#### Installation

**On Debian/Ubuntu:**

```bash
apt-get install snmp
```

**On RHEL/CentOS:**

```bash
yum install net-snmp-utils
```

**On macOS:**

```bash
brew install net-snmp
```

**On Windows:** Download from [Net-SNMP website](http://www.net-snmp.org/download.html)

#### Basic Usage

```bash
snmpwalk -v [1|2c|3] -c [community] [host] [OID]
```

#### Common Parameters

- `-v`: SNMP version (1, 2c, or 3)
- `-c`: Community string (default is "public")
- `-O`: Output format (e.g., `-Of` for full OIDs)
- `-t`: Timeout period
- `-r`: Number of retries
- `-m`: MIB files to use
- `-M`: Directory for MIB files

#### Practical Examples

**Basic system information:**

```bash
snmpwalk -v 2c -c public 192.168.1.1 system
```

**Hardware and software inventory:**

```bash
snmpwalk -v 2c -c public 192.168.1.1 hrSWInstalledName
snmpwalk -v 2c -c public 192.168.1.1 hrDeviceDescr
```

**Network interfaces:**

```bash
snmpwalk -v 2c -c public 192.168.1.1 interfaces
```

**Routing information:**

```bash
snmpwalk -v 2c -c public 192.168.1.1 ipRouteTable
```

**Use specific MIB:**

```bash
snmpwalk -v 2c -c public -m ALL 192.168.1.1 SNMPv2-MIB::system
```

#### Troubleshooting

- **Timeout errors**: Check network connectivity and firewall settings
- **No response**: Verify SNMP is enabled and the community string is correct
- **Permission denied**: Ensure proper access control lists are configured
- **Error parsing MIB**: Check MIB file format and dependencies

### 2. SNMP-Check

#### Overview

SNMP-Check is a free and open-source tool that collects information from devices via SNMP and provides detailed, well-organized output.

#### Installation

**On Kali Linux:**

```bash
apt-get install snmp-check
```

**From GitHub:**

```bash
git clone https://github.com/pwnsauce8/snmpcheck.git
cd snmpcheck
gem install snmp
chmod +x snmpcheck.rb
```

#### Basic Usage

```bash
snmp-check [options] <target IP address>
```

#### Common Parameters

- `-c`: Community string (default is "public")
- `-v`: SNMP version (default is 1)
- `-w`: Write community string for testing
- `-p`: SNMP port (default is 161)
- `-d`: Enable detailed mode
- `-t`: Timeout in seconds
- `-r`: Number of retries
- `-a`: Make all tests

#### Practical Examples

**Basic scan:**

```bash
snmp-check 192.168.1.1
```

**Detailed scan:**

```bash
snmp-check -d 192.168.1.1
```

**Using non-standard community string:**

```bash
snmp-check -c private 192.168.1.1
```

**Comprehensive scan with version 2c:**

```bash
snmp-check -v 2c -a -d 192.168.1.1
```

#### Output Information

- System information
- Network information
- Network services
- Processes
- Storage information
- File system information
- Device information
- Software components
- User accounts (if available)
- TCP/UDP connections

#### Troubleshooting

- **Connection errors**: Verify target IP and port
- **Authentication failures**: Check community string
- **Partial information**: Some devices restrict SNMP information access
- **Slow scanning**: Use `-t` to increase timeout for slow networks

### 3. Onesixtyone

#### Overview

Onesixtyone is a fast SNMP scanner designed to identify community strings on SNMP-enabled devices. It's particularly useful during the reconnaissance phase of a security assessment.

#### Installation

**On Kali Linux:**

```bash
apt-get install onesixtyone
```

**From GitHub:**

```bash
git clone https://github.com/trailofbits/onesixtyone.git
cd onesixtyone
make
```

#### Basic Usage

```bash
onesixtyone [options] <target>
```

#### Common Parameters

- `-c`: File with community names
- `-i`: File with target addresses
- `-o`: Output file
- `-d`: Debug mode
- `-w`: Wait time in milliseconds between packets
- `-v`: Verbose mode

#### Practical Examples

**Scan a single host with default wordlist:**

```bash
onesixtyone 192.168.1.1
```

**Scan a network range with custom community strings:**

```bash
onesixtyone -c community.txt -i hosts.txt
```

**Scan with slower sending rate (for unstable networks):**

```bash
onesixtyone -w 100 192.168.1.1
```

#### Creating Target and Community Files

**hosts.txt example:**

```
192.168.1.1
192.168.1.2
192.168.1.3
```

**community.txt example:**

```
public
private
manager
admin
cisco
community
```

#### Troubleshooting

- **No results**: Check if targets are reachable and running SNMP
- **Packet loss**: Use `-w` to increase wait time between packets
- **False negatives**: Try different community string wordlists
- **Port filtering**: Verify SNMP port (161) is not filtered

### 4. SNMP Enum

#### Overview

SNMP Enum (snmpenum.pl) is a Perl script designed to enumerate information from SNMP-enabled devices, with a focus on extracting user accounts from Windows systems.

#### Installation

```bash
git clone https://github.com/penetration-testing/snmpenum.git
cd snmpenum
chmod +x snmpenum.pl
```

#### Prerequisites

```bash
cpan Net::SNMP
```

#### Basic Usage

```bash
./snmpenum.pl <target IP> <community string> <config file>
```

#### Configuration Files

- **windows.txt**: For Windows account enumeration
- **linux.txt**: For Linux system information
- **cisco.txt**: For Cisco device enumeration

#### Practical Examples

**Windows user enumeration:**

```bash
./snmpenum.pl 192.168.1.1 public windows.txt
```

**Linux system information:**

```bash
./snmpenum.pl 192.168.1.1 public linux.txt
```

**Custom OID list:**

```bash
# Create custom.txt with desired OIDs
./snmpenum.pl 192.168.1.1 public custom.txt
```

#### Troubleshooting

- **Perl module errors**: Install required modules with CPAN
- **Script crashes**: Update the script for newer Perl versions
- **No output**: Verify SNMP access and community string
- **Configuration errors**: Check format of the config file

### 5. SNMPv3 Enumeration Tools

#### Overview

SNMPv3 provides stronger security with authentication and encryption. These tools specifically target or support SNMPv3 enumeration.

#### 5.1 SNMPwalk for SNMPv3

```bash
snmpwalk -v 3 -l [secLevel] -u [username] -a [authProtocol] -A [authPassword] -x [privProtocol] -X [privPassword] [host] [OID]
```

**Parameters:**

- `-l`: Security level (noAuthNoPriv, authNoPriv, authPriv)
- `-u`: Security name (username)
- `-a`: Authentication protocol (MD5 or SHA)
- `-A`: Authentication password
- `-x`: Privacy protocol (DES or AES)
- `-X`: Privacy password

**Example:**

```bash
snmpwalk -v 3 -l authPriv -u admin -a SHA -A authpass -x AES -X privpass 192.168.1.1 system
```

#### 5.2 SNMP-Check for SNMPv3

```bash
snmp-check -v 3 -u [username] -l [secLevel] -a [authProtocol] -A [authPassword] -x [privProtocol] -X [privPassword] [host]
```

**Example:**

```bash
snmp-check -v 3 -u admin -l authPriv -a SHA -A authpass -x AES -X privpass 192.168.1.1
```

#### 5.3 SNMPv3 Enumeration with Metasploit

```
use auxiliary/scanner/snmp/snmp_enum
set RHOSTS 192.168.1.1
set VERSION 3
set USERNAME admin
set AUTHPASS authpass
set PRIVPASS privpass
set AUTHPROTO SHA
set PRIVPROTO AES
run
```

#### Troubleshooting SNMPv3

- **Authentication errors**: Verify username, authentication protocol, and password
- **Encryption errors**: Check privacy protocol and password
- **Version mismatch**: Ensure target supports SNMPv3
- **Parameter order**: Some tools require parameters in specific order

### 6. Braa

#### Overview

Braa is a mass SNMP scanner capable of querying hundreds or thousands of devices simultaneously, making it ideal for large network assessments.

#### Installation

**On Kali Linux:**

```bash
apt-get install braa
```

**From Source:**

```bash
git clone https://github.com/mteg/braa.git
cd braa
make
```

#### Basic Usage

```bash
braa [community@]host[:port]:oid[/type][=value] ...
```

#### Common Parameters

- `community@host`: Community string and target
- `:oid`: The OID to query
- `/type`: Data type (optional)
- `=value`: For SNMP SET operations

#### Practical Examples

**Query system description from multiple hosts:**

```bash
braa public@192.168.1.1:.1.3.6.1.2.1.1.1.0 public@192.168.1.2:.1.3.6.1.2.1.1.1.0
```

**Query multiple OIDs from one host:**

```bash
braa public@192.168.1.1:.1.3.6.1.2.1.1.1.0 public@192.168.1.1:.1.3.6.1.2.1.1.3.0
```

**Using a file with targets:**

```bash
# Create targets.txt with "community@host:oid" entries
braa < targets.txt
```

**Setting a value (if write access is available):**

```bash
braa public@192.168.1.1:.1.3.6.1.2.1.1.4.0=admin@example.com
```

#### Troubleshooting

- **Syntax errors**: Double check the complex syntax format
- **Timeout errors**: Adjust timeout with `-t` parameter
- **Limited results**: Some devices may block mass queries
- **Performance issues**: Reduce number of simultaneous queries

### 7. SNMP Nmap Scripts

#### Overview

Nmap includes several NSE (Nmap Scripting Engine) scripts specifically designed for SNMP enumeration that provide a convenient way to gather SNMP information during network scans.

#### Basic Usage

```bash
nmap -sU -p 161 --script=snmp-* [target]
```

#### Available SNMP Scripts

- **snmp-brute**: Attempts to find community strings
- **snmp-info**: Basic information about the SNMP server
- **snmp-interfaces**: Enumerates network interfaces
- **snmp-netstat**: Equivalent of netstat command
- **snmp-processes**: Enumerates running processes
- **snmp-sysdescr**: System description
- **snmp-win32-services**: Enumerates Windows services
- **snmp-win32-shares**: Enumerates Windows shares
- **snmp-win32-software**: Lists installed software
- **snmp-win32-users**: Enumerates Windows users

#### Practical Examples

**Basic SNMP scan:**

```bash
nmap -sU -p 161 --script=snmp-info 192.168.1.1
```

**Brute force community strings:**

```bash
nmap -sU -p 161 --script=snmp-brute 192.168.1.1
```

**Comprehensive SNMP enumeration:**

```bash
nmap -sU -p 161 --script=snmp-* 192.168.1.1
```

**Target Windows systems:**

```bash
nmap -sU -p 161 --script=snmp-win32-* 192.168.1.1
```

**Custom community string:**

```bash
nmap -sU -p 161 --script=snmp-* --script-args snmpcommunity=private 192.168.1.1
```

#### Troubleshooting

- **Script errors**: Update Nmap to latest version
- **Missing results**: Verify SNMP access and community string
- **Script timeout**: Use `--script-timeout` to increase timeout
- **Performance issues**: Run fewer scripts simultaneously

### 8. Metasploit SNMP Modules

#### Overview

Metasploit Framework includes multiple modules specifically designed for SNMP enumeration and exploitation, providing a comprehensive toolset within a penetration testing framework.

#### Key Modules

- **auxiliary/scanner/snmp/snmp_login**: Brute force community strings
- **auxiliary/scanner/snmp/snmp_enum**: General SNMP enumeration
- **auxiliary/scanner/snmp/snmp_enumusers**: Enumerate user accounts
- **auxiliary/scanner/snmp/snmp_enumshares**: Enumerate network shares
- **auxiliary/scanner/snmp/snmp_enumprinters**: Enumerate printers
- **auxiliary/scanner/snmp/snmp_enumprocesses**: Enumerate processes

#### Basic Usage

```
msfconsole
use auxiliary/scanner/snmp/snmp_enum
set RHOSTS 192.168.1.1
set COMMUNITY public
run
```

#### Practical Examples

**Brute force community strings:**

```
use auxiliary/scanner/snmp/snmp_login
set RHOSTS 192.168.1.0/24
set THREADS 10
run
```

**Enumerate users from Windows hosts:**

```
use auxiliary/scanner/snmp/snmp_enumusers
set RHOSTS 192.168.1.1
set COMMUNITY public
run
```

**Scan an IP range:**

```
use auxiliary/scanner/snmp/snmp_enum
set RHOSTS 192.168.1.0/24
set COMMUNITY public
set THREADS 10
run
```

#### Troubleshooting

- **Connection errors**: Verify network connectivity and firewall settings
- **Authentication failures**: Check community string
- **Module errors**: Update Metasploit Framework
- **Incomplete results**: Some MIBs may not be supported by target devices

## Common SNMP MIBs and OIDs

### System Information

- **System Description**: .1.3.6.1.2.1.1.1.0
- **System Name**: .1.3.6.1.2.1.1.5.0
- **System Location**: .1.3.6.1.2.1.1.6.0
- **System Contact**: .1.3.6.1.2.1.1.4.0
- **System Uptime**: .1.3.6.1.2.1.1.3.0

### Network Interfaces

- **Interface Description**: .1.3.6.1.2.1.2.2.1.2
- **Interface Type**: .1.3.6.1.2.1.2.2.1.3
- **Interface Status**: .1.3.6.1.2.1.2.2.1.8
- **Interface MAC Address**: .1.3.6.1.2.1.2.2.1.6
- **Interface IP Address**: .1.3.6.1.2.1.4.20.1.1

### Routing Information

- **Routing Table**: .1.3.6.1.2.1.4.21.1
- **IP Routing Destination**: .1.3.6.1.2.1.4.21.1.1
- **IP Routing Mask**: .1.3.6.1.2.1.4.21.1.11
- **IP Routing Next Hop**: .1.3.6.1.2.1.4.21.1.7

### Windows-Specific

- **Running Processes**: .1.3.6.1.2.1.25.4.2.1.2
- **Installed Software**: .1.3.6.1.2.1.25.6.3.1.2
- **Storage Units**: .1.3.6.1.2.1.25.2.3.1
- **System Users**: .1.3.6.1.4.1.77.1.2.25

### Cisco-Specific

- **Cisco Configuration**: .1.3.6.1.4.1.9.9.96.1.1.1.1.5
- **Cisco Memory Pool**: .1.3.6.1.4.1.9.9.48.1.1.1
- **Cisco CPU Usage**: .1.3.6.1.4.1.9.9.109.1.1.1.1.5
- **Cisco Interface Status**: .1.3.6.1.4.1.9.9.42.1.2.1.1.3

## Real-World Use Cases

### 1. Network Device Inventory

```
Scenario: Creating a comprehensive inventory of all network devices
Tools: SNMPwalk, SNMP-Check
Process:
1. Discover devices with active SNMP using Nmap
2. Enumerate device details using SNMPwalk
3. Extract hardware and software information using SNMP-Check
4. Compile inventory in spreadsheet or database
```

### 2. Security Assessment

```
Scenario: Identifying SNMP security weaknesses during a penetration test
Tools: Onesixtyone, Metasploit SNMP modules
Process:
1. Scan for SNMP-enabled devices using Nmap
2. Brute force community strings with Onesixtyone
3. Enumerate sensitive information using Metasploit modules
4. Test for write access to critical OIDs
5. Document findings and recommendations
```

### 3. Network Monitoring Setup

```
Scenario: Preparing for implementing a network monitoring solution
Tools: SNMPwalk, Braa
Process:
1. Identify devices requiring monitoring
2. Verify SNMP accessibility and community strings
3. Determine available OIDs and their values
4. Configure monitoring solution based on findings
```

### 4. Troubleshooting Network Issues

```
Scenario: Diagnosing network performance problems
Tools: SNMPwalk, Nmap SNMP scripts
Process:
1. Identify problematic network segments
2. Query interface statistics using SNMPwalk
3. Check for errors, discards, and bandwidth utilization
4. Identify routing inconsistencies
5. Monitor real-time changes in network traffic
```

### 5. Change Management Verification

```
Scenario: Verifying network changes were applied correctly
Tools: SNMPwalk, SNMP-Check
Process:
1. Capture baseline configuration before changes
2. Implement planned changes
3. Capture post-change configuration
4. Compare configurations to verify changes
5. Document results for change management records
```

## Best Practices

### 1. Ethical Considerations

- Always obtain proper authorization before scanning
- Document all enumeration activities
- Minimize impact on production systems
- Report discovered vulnerabilities through proper channels
- Follow responsible disclosure guidelines

### 2. Technical Approach

- Start with passive techniques before active scanning
- Begin with basic queries before comprehensive enumeration
- Use rate limiting to prevent overwhelming devices
- Avoid repeated queries to the same device
- Schedule intensive scans during low-traffic periods

### 3. Security Recommendations

- Disable SNMP if not required
- Upgrade to SNMPv3 where possible
- Use strong credentials for SNMPv3
- Implement access control lists for SNMP traffic
- Use non-default community strings
- Limit accessible OIDs to only what's necessary
- Monitor for unauthorized SNMP queries

### 4. Efficient Enumeration

- Focus on high-value targets and information
- Create custom OID lists for specific use cases
- Automate regular enumeration tasks with scripts
- Store and analyze results in structured formats
- Use parallelization for large networks (tools like Braa)

## Advanced Techniques

### 1. Custom SNMP Enumeration Scripts

#### Python Example using PySNMP

```python
#!/usr/bin/env python3
from pysnmp.hlapi import *

def snmp_get(host, community, oid):
    errorIndication, errorStatus, errorIndex, varBinds = next(
        getCmd(SnmpEngine(),
               CommunityData(community),
               UdpTransportTarget((host, 161)),
               ContextData(),
               ObjectType(ObjectIdentity(oid)))
    )
    
    if errorIndication:
        print(f"Error: {errorIndication}")
        return None
    elif errorStatus:
        print(f"Error: {errorStatus.prettyPrint()} at {errorIndex}")
        return None
    else:
        for varBind in varBinds:
            return varBind[1]

def snmp_walk(host, community, oid):
    results = []
    for (errorIndication,
         errorStatus,
         errorIndex,
         varBinds) in nextCmd(SnmpEngine(),
                              CommunityData(community),
                              UdpTransportTarget((host, 161)),
                              ContextData(),
                              ObjectType(ObjectIdentity(oid)),
                              lexicographicMode=False):
        
        if errorIndication:
            print(f"Error: {errorIndication}")
            break
        elif errorStatus:
            print(f"Error: {errorStatus.prettyPrint()} at {errorIndex}")
            break
        else:
            for varBind in varBinds:
                results.append((str(varBind[0]), str(varBind[1])))
    
    return results

# Example usage
if __name__ == "__main__":
    host = "192.168.1.1"
    community = "public"
    
    # Get system information
    system_name = snmp_get(host, community, '1.3.6.1.2.1.1.5.0')
    system_description = snmp_get(host, community, '1.3.6.1.2.1.1.1.0')
    
    print(f"System Name: {system_name}")
    print(f"System Description: {system_description}")
    
    # Walk network interfaces
    print("\nNetwork Interfaces:")
    interfaces = snmp_walk(host, community, '1.3.6.1.2.1.2.2.1.2')
    for idx, interface in enumerate(interfaces, 1):
        print(f"{idx}. {interface[1]}")
    
    # Walk running processes (for systems that support it)
    print("\nRunning Processes:")
    processes = snmp_walk(host, community, '1.3.6.1.2.1.25.4.2.1.2')
    for idx, process in enumerate(processes, 1):
        print(f"{idx}. {process[1]}")
```

### 2. SNMP Trap Analysis

SNMP traps are notifications sent by devices to management systems. Analyzing these can provide valuable information.

#### Setting up a basic SNMP trap receiver

```bash
# Using snmptrapd from Net-SNMP
snmptrapd -f -Lo
```

#### Configuring snmptrapd (/etc/snmp/snmptrapd.conf)

```
authCommunity log,execute,net public
format1 %V\n%v\n%W\n%w\n%X\n Agent Address: %A\n%B\n%N\n%O\n%P\n%Q\n%R\n%S\n%T\n%G\n
traphandle default /usr/local/bin/snmptrap_handler.sh
```

#### Example trap handler script

```bash
#!/bin/bash
# /usr/local/bin/snmptrap_handler.sh
# Simple trap handler that logs traps to a file

LOG_FILE="/var/log/snmptraps.log"

# Get trap data from stdin
while read line
do
    echo "$(date): $line" >> $LOG_FILE
done

# Optionally process specific trap types
if grep -q "linkDown" $LOG_FILE; then
    # Handle link down event
    echo "Link down detected" >> $LOG_FILE
fi
```

### 3. SNMP-Based Network Mapping

Creating network topology maps using SNMP data:

#### Using Bridge MIB and CDP/LLDP information

```bash
# Get bridge forwarding table
snmpwalk -v 2c -c public 192.168.1.1 .1.3.6.1.2.1.17.4.3.1.2

# Get CDP neighbors on Cisco devices
snmpwalk -v 2c -c public 192.168.1.1 .1.3.6.1.4.1.9.9.23.1.2.1.1

# Get LLDP neighbors
snmpwalk -v 2c -c public 192.168.1.1 .1.0.8802.1.1.2.1.4
```

#### Processing data with Python to create network graph

```python
import networkx as nx
import matplotlib.pyplot as plt
from pysnmp.hlapi import *

# Create network graph
G = nx.Graph()

def get_neighbors(host, community):
    neighbors = []
    # Process CDP neighbors (Cisco)
    for (errorIndication, errorStatus, errorIndex, varBinds) in nextCmd(
            SnmpEngine(),
            CommunityData(community),
            UdpTransportTarget((host, 161)),
            ContextData(),
            ObjectType(ObjectIdentity('1.3.6.1.4.1.9.9.23.1.2.1.1.6')),
            lexicographicMode=False):
        
        if errorIndication or errorStatus:
            continue
        
        for varBind in varBinds:
            # Extract neighbor information
            neighbors.append(str(varBind[1]))
    
    return neighbors

# Add nodes and edges to the graph
def map_network(seed_device, community):
    devices_scanned = set()
    devices_to_scan = {seed_device}
    
    while devices_to_scan:
        current_device = devices_to_scan.pop()
        if current_device in devices_scanned:
            continue
        
        print(f"Scanning {current_device}")
        G.add_node(current_device)
        devices_scanned.add(current_device)
        
        neighbors = get_neighbors(current_device, community)
        for neighbor in neighbors:
            G.add_edge(current_device, neighbor)
            if neighbor not in devices_scanned:
                devices_to_scan.add(neighbor)
    
    return G

# Generate and visualize the network map
network = map_network("192.168.1.1", "public")
nx.draw(network, with_labels=True)
plt.savefig("network_map.png")
plt.show()
```

## Comparison of SNMP Enumeration Tools

|Tool|Interface|Speed|Comprehensive|SNMPv3 Support|Output Formats|Platform|
|---|---|---|---|---|---|---|
|SNMPwalk|CLI|Moderate|High|Yes|Text|Windows, Linux, macOS|
|SNMP-Check|CLI|Moderate|High|Yes|Text|Linux, macOS|
|Onesixtyone|CLI|Very Fast|Low|No|Text|Linux, macOS|
|SNMP Enum|CLI|Moderate|Medium|No|Text|Linux, macOS|
|Braa|CLI|Very Fast|Medium|No|Text|Linux|
|Nmap SNMP Scripts|CLI|Fast|High|Limited|Text, XML|Windows, Linux, macOS|
|Metasploit Modules|CLI/Console|Moderate|High|Yes|Text, Database|Windows, Linux, macOS|
|Custom Python Scripts|CLI|Customizable|Customizable|Yes|Customizable|Windows, Linux, macOS|

## Defensive Measures Against Unauthorized SNMP Enumeration

### 1. SNMP Hardening

- **Upgrade to SNMPv3**: Implement authentication and encryption
- **Change community strings**: Use complex, non-default community strings
- **Implement access control**: Restrict SNMP access to management stations
- **Configure read-only access**: Prevent modification of device configuration
- **Disable unused SNMP versions**: Disable SNMPv1 and SNMPv2c if possible

### 2. Network-Level Protection

- **Use access control lists**: Restrict SNMP traffic to authorized management stations
- **Implement SNMP over VPN**: Tunnel SNMP traffic through VPN for external management
- **Firewall rules**: Block SNMP ports (161/UDP and 162/UDP) at network boundaries
- **Use a separate management VLAN**: Isolate SNMP traffic from regular network traffic
- **Network segmentation**: Apply principle of least privilege to SNMP access

### 3. Monitoring and Detection

- **Log SNMP requests**: Enable logging of all SNMP queries
- **Configure SNMP traps**: Set up notifications for authentication failures
- **Implement IDS/IPS rules**: Create signatures for SNMP scanning tools
- **Regular auditing**: Review SNMP configurations and access logs
- **Honeypots**: Deploy SNMP honeypots to detect reconnaissance activities

### 4. SNMP Configuration Best Practices

- **Minimal exposure**: Only expose necessary OIDs
- **Regular updates**: Keep SNMP implementations patched
- **Strong authentication**: Use strong passwords for SNMPv3
- **Implement view-based access**: Restrict visible OIDs based on user roles
- **Secure trap receivers**: Ensure trap receivers are properly secured

## Resources

- [Net-SNMP Documentation](http://www.net-snmp.org/docs/)
- [SNMP RFCs (RFC 3411-3418)](https://tools.ietf.org/html/rfc3411)
- [IANA SNMP Number Assignments](https://www.iana.org/assignments/enterprise-numbers/enterprise-numbers)
- [Cisco SNMP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/snmp/configuration/xe-16/snmp-xe-16-book.html)
- [Common Vulnerability Scoring SNMP Issues](https://nvd.nist.gov/vuln/search/results?form_type=Basic&results_type=overview&query=snmp&search_type=all)
- [OID Repository](http://oid-info.com/)
- [MIB Browser Tools](https://www.manageengine.com/products/mibbrowser-free-tool/)