## Overview

Slitheris Network Scanner is a powerful network discovery and management tool developed by Komodo Labs. It provides detailed hardware and software information about networked devices, making it an essential tool for network administrators, IT professionals, and security analysts.

## Key Features

- **Deep Network Discovery**: Identifies active devices across subnets without requiring installation on target machines
- **Detailed Hardware Information**: Collects comprehensive hardware specs including processors, memory, storage, and peripherals
- **Software Inventory**: Scans and catalogs installed applications, services, and Windows updates
- **Network Topology Mapping**: Creates visual maps of network connections and relationships
- **Switch Port Mapping**: Identifies which devices are connected to specific ports on network switches
- **Agentless Operation**: Functions without installing agents on target devices
- **Real-time Monitoring**: Tracks network changes as they occur
- **Exportable Reports**: Generates detailed reports in various formats (PDF, CSV, Excel)
- **Custom Scanning Profiles**: Creates tailored scanning configurations for different networks or use cases

## Installation

### System Requirements

- **Operating System**: Windows 10/11 or Windows Server 2016/2019/2022
- **Processor**: Dual-core 2GHz+ processor
- **Memory**: 4GB RAM minimum (8GB recommended)
- **Storage**: 1GB free disk space
- **Network**: Admin privileges on the network to be scanned

### Installation Steps

1. Download the installer from the official Komodo Labs website
2. Run the installer with administrative privileges
3. Follow the installation wizard
4. Enter your license key when prompted (or select the trial option)
5. Complete installation and launch the application

### Licensing Options

- **Free Trial**: Limited functionality for evaluation purposes
- **Professional License**: Full functionality for individual users
- **Enterprise License**: Network-wide deployment with centralized management

## Basic Usage

### Initial Setup

1. Launch Slitheris Network Scanner
2. Select "New Scan" from the main interface
3. Configure the scan parameters:
    - IP range or subnet to scan
    - Scan depth level
    - Authentication credentials (for deeper scans)
4. Click "Start Scan" to begin discovery

### Performing a Quick Scan

```
1. Select "Quick Scan" from the main menu
2. Enter the IP range (e.g., 192.168.1.0/24)
3. Click "Start"
```

### Configuring a Detailed Scan

```
1. Select "Advanced Scan" from the main menu
2. Configure the following parameters:
   - Target IP range
   - Scan types (hardware, software, services)
   - Authentication credentials
   - Scan frequency (one-time vs. recurring)
3. Click "Start Scan"
```

### Saving Scan Configurations

```
1. Configure scan parameters
2. Click "Save Configuration"
3. Name your configuration profile
4. Access saved configurations from the "Profiles" menu
```

## Advanced Usage

### Using Scan Templates

Slitheris provides several pre-configured templates:

- **Basic Discovery**: Identifies active devices with minimal information
- **Hardware Inventory**: Focuses on detailed hardware specifications
- **Software Audit**: Catalogs installed applications and services
- **Security Assessment**: Identifies potential vulnerabilities and misconfigurations
- **Custom**: Create your own template based on specific requirements

### Scheduling Recurring Scans

```
1. Configure scan parameters
2. Select "Schedule" option
3. Set frequency (daily, weekly, monthly)
4. Specify time and notification preferences
5. Click "Save Schedule"
```

### Switch Port Mapping

```
1. Enable "Switch Discovery" in scan options
2. Provide SNMP credentials for network switches
3. Run the scan
4. View results in the "Switch Mapping" section
```

### Working with Credentials

For deeper scans, Slitheris can use authentication:

```
1. Go to "Credentials Manager"
2. Add Windows domain or local credentials
3. Add SNMP community strings
4. Add SSH credentials for Linux/Unix systems
5. Apply specific credentials to scans as needed
```

### Exporting Results

```
1. Complete a network scan
2. Select "Export" from the results view
3. Choose format (PDF, CSV, Excel, XML)
4. Select data fields to include
5. Save the report to your desired location
```

## Troubleshooting

### Common Issues and Solutions

#### Scan Does Not Discover All Devices

- **Cause**: Firewall settings or network segmentation
- **Solution**:
    1. Verify firewall settings allow ICMP and WMI traffic
    2. Check network routing between scanner and target devices
    3. Try scanning with different protocols enabled

#### Authentication Failures

- **Cause**: Incorrect credentials or insufficient privileges
- **Solution**:
    1. Verify username and password
    2. Ensure account has administrative access
    3. Check domain policy restrictions

#### Slow Scan Performance

- **Cause**: Scanning too many devices simultaneously or network congestion
- **Solution**:
    1. Reduce scan scope or break into smaller subnets
    2. Adjust concurrency settings in "Scan Options"
    3. Schedule scans during off-peak hours

#### Incomplete Hardware Information

- **Cause**: Insufficient access rights or WMI issues
- **Solution**:
    1. Use credentials with administrative access
    2. Check if WMI service is running on target devices
    3. Enable "Deep Hardware Scan" option

#### Application Crashes

- **Cause**: Resource limitations or database corruption
- **Solution**:
    1. Close other applications to free resources
    2. Repair installation through the installer
    3. Verify database integrity in "Settings > Maintenance"

### Understanding Scan Results

#### Device Status Indicators

- **Green**: Device is online and fully scanned
- **Yellow**: Device is online but incomplete information
- **Red**: Device is offline or unreachable
- **Gray**: Device status unknown or pending scan

#### Error Codes

- **1001**: Authentication failure
- **1002**: WMI access denied
- **1003**: Firewall blocking
- **1004**: Service unavailable
- **1005**: Timeout during scan

## Real-World Use Cases

### 1. IT Asset Management

```
Configuration:
- Full network scan (192.168.0.0/16)
- Deep hardware and software inventory
- Weekly scheduled scans
- Differential reporting
```

Use case: Maintaining accurate inventory of all IT assets across the organization for budgeting, planning, and compliance.

### 2. Network Security Audit

```
Configuration:
- Target specific subnets
- Enable vulnerability assessment
- Check for unauthorized devices
- Generate compliance reports
```

Use case: Identifying potential security risks and unauthorized devices on the network as part of regular security audits.

### 3. Troubleshooting Network Issues

```
Configuration:
- Rapid scan of affected subnet
- Focus on connectivity and basic information
- Compare with baseline scan
```

Use case: Quickly identifying changes or issues when network problems occur.

### 4. Software License Compliance

```
Configuration:
- Focus on software inventory
- Generate detailed software reports
- Compare against licensed software database
```

Use case: Ensuring all software in use is properly licensed and identifying potential compliance issues.

### 5. Network Documentation

```
Configuration:
- Complete network scan
- Enable topology mapping
- Export detailed reports with diagrams
```

Use case: Creating comprehensive documentation of network infrastructure for planning and disaster recovery purposes.

## Best Practices

1. **Start with Limited Scans**: Begin with smaller subnets before scanning entire networks
2. **Use Appropriate Credentials**: Create a dedicated service account with necessary privileges
3. **Schedule Off-Hours Scans**: Minimize impact on network performance and users
4. **Establish Baselines**: Perform regular scans to track changes over time
5. **Secure Scan Results**: Protect exported reports as they contain sensitive information
6. **Regular Updates**: Keep Slitheris updated to the latest version
7. **Document Custom Configurations**: Maintain documentation of custom scan profiles
8. **Validate Results**: Periodically verify scan accuracy through spot checks

## Command Line Interface (CLI)

Slitheris offers a CLI for automation and integration:

```bash
# Basic scan
slitheris-cli.exe --scan --range 192.168.1.0/24 --output report.csv

# Scheduled scan with authentication
slitheris-cli.exe --scan --range 10.0.0.0/16 --auth domain\user:password --schedule daily

# Export specific information
slitheris-cli.exe --export --type hardware --format xml --output hardware.xml

# Quiet mode for scripting
slitheris-cli.exe --scan --range 192.168.1.0/24 --quiet --exit-on-complete
```

## Integration with Other Tools

### PowerShell Integration

```powershell
# Example PowerShell script to automate Slitheris scans
$scanOutput = & "C:\Program Files\Slitheris\slitheris-cli.exe" --scan --range 192.168.1.0/24 --output scan.xml
# Process the results
if ($LASTEXITCODE -eq 0) {
    [xml]$results = Get-Content scan.xml
    # Process the XML data
}
```

### SIEM Integration

Slitheris can export to formats compatible with Security Information and Event Management systems:

```
1. Configure export in Syslog format
2. Direct output to SIEM collection point
3. Create alerts based on device changes
```

### Ticketing System Integration

```
1. Configure scan to generate reports
2. Use CLI with scripts to process results
3. Create tickets automatically for issues detected
```

## Comparison with Similar Tools

|Feature|Slitheris|Nmap|Angry IP Scanner|Advanced IP Scanner|
|---|---|---|---|---|
|Hardware Detection|Excellent|Limited|None|Good|
|Software Inventory|Extensive|Limited|None|Basic|
|Agentless Scanning|Yes|Yes|Yes|Yes|
|Switch Port Mapping|Yes|No|No|Limited|
|Ease of Use|Moderate|Complex|Simple|Simple|
|Reporting|Extensive|Basic|Basic|Moderate|
|Price|Commercial|Free|Free|Free|

## Advanced Configuration

### Custom WMI Queries

Slitheris allows you to create custom WMI queries for specialized information:

```
1. Go to "Settings > Advanced > Custom Queries"
2. Add new query with WMI syntax
3. Name and categorize the query
4. Enable it in scan profiles
```

### Network Traffic Optimization

```
1. Access "Settings > Network"
2. Adjust concurrent connections (lower for slower networks)
3. Set packet timeout values
4. Configure bandwidth throttling during business hours
```

### Database Maintenance

```
1. Go to "Tools > Database Maintenance"
2. Options include:
   - Compact database
   - Purge old scan data
   - Backup database
   - Verify integrity
```

## Resources

- [Official Komodo Labs Website](https://www.komodolabs.com)
- [User Manual](https://www.komodolabs.com/documentation)
- [Knowledge Base](https://support.komodolabs.com)
- [Video Tutorials](https://www.komodolabs.com/tutorials)
- [Support Forum](https://forum.komodolabs.com)