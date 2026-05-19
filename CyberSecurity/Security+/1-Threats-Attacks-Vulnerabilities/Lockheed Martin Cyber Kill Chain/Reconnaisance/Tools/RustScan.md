## Overview

RustScan is a modern port scanning tool written in Rust that aims to be faster and more efficient than traditional tools like Nmap. It acts as a port discovery tool that automatically pipes found open ports into Nmap for deeper analysis.

## Key Features

- **Speed**: Scans all 65,535 ports in under a second by default
- **Configurable**: Easily adjust batch sizes, timeouts, and ports to scan
- **Nmap Integration**: Seamlessly passes discovered ports to Nmap for deeper inspection
- **Lightweight**: Minimal resource footprint compared to traditional scanners
- **Script Support**: Runs custom scripts on open ports
- **Docker Support**: Available as a Docker container for easy deployment

## Installation

### Method 1: Using Cargo (Recommended for Rust users)

```bash
cargo install rustscan
```

### Method 2: Using Homebrew (macOS and Linux)

```bash
brew install rustscan
```

### Method 3: Using Docker

```bash
docker pull rustscan/rustscan
docker run -it rustscan/rustscan
```

### Method 4: Building from Source

```bash
git clone https://github.com/RustScan/RustScan.git
cd RustScan
cargo build --release
./target/release/rustscan
```

## Basic Usage

### Quick Scan of a Target

```bash
rustscan -a 192.168.1.1
```

### Scan Multiple Targets

```bash
rustscan -a 192.168.1.1,192.168.1.2,192.168.1.3
```

or

```bash
rustscan -a 192.168.1.0/24
```

### Scan Specific Ports

```bash
rustscan -a 192.168.1.1 -p 80,443,8080
```

### Scan Port Ranges

```bash
rustscan -a 192.168.1.1 -p 1-1000
```

### Adjusting Scan Speed (Batch Size)

The batch size determines how many ports are scanned simultaneously:

```bash
rustscan -a 192.168.1.1 -b 500
```

### Set Timeout (in milliseconds)

```bash
rustscan -a 192.168.1.1 --timeout 5000
```

### Full Scan with Nmap Integration

```bash
rustscan -a 192.168.1.1 -- -A -sC -sV
```

(Everything after `--` is passed directly to Nmap)

## Advanced Usage

### Using Scripts

```bash
rustscan -a 192.168.1.1 --scripts http
```

### Using Custom Configuration File

```bash
rustscan -a 192.168.1.1 --config config.toml
```

### Greppable Output

```bash
rustscan -a 192.168.1.1 -g
```

### JSON Output

```bash
rustscan -a 192.168.1.1 --json
```

### Accessible Mode (More Human-Readable)

```bash
rustscan -a 192.168.1.1 --accessible
```

## Troubleshooting

### Common Issues and Solutions

#### Too Many Open Files Error

If you encounter "Too many open files" errors:

1. Check your current limit:

```bash
ulimit -n
```

2. Temporarily increase the limit:

```bash
ulimit -n 10000
```

3. Or reduce the batch size:

```bash
rustscan -a 192.168.1.1 -b 100
```

#### Connection Refused or Connection Timed Out

- Increase the timeout:

```bash
rustscan -a 192.168.1.1 --timeout 5000
```

- The target might be blocking or dropping scan packets (firewall)

#### High CPU/Memory Usage

- Reduce the batch size:

```bash
rustscan -a 192.168.1.1 -b 50
```

#### Scan Taking Too Long

- Increase the batch size (if system resources allow):

```bash
rustscan -a 192.168.1.1 -b 1000
```

#### False Positives/Negatives

- Verify findings with a slower, more thorough scan:

```bash
rustscan -a 192.168.1.1 --timeout 5000 -- -sV
```

### Interpreting Results

#### Sample Output

```
.----. .-. .-. .----..---.  .----. .---.   .--.  .-. .-.
| {}  }| { } |{ {__ {_   _}{ {__  /  ___} / {} \ |  `| |
| .-. \| {_} |.-._} } | |  .-._} }\     }/  /\  \| |\  |
`-' `-'`-----'`----'  `-'  `----'  `---' `-'  `-'`-' `-'
The Modern Day Port Scanner.
________________________________________
: https://github.com/RustScan/RustScan :
 --------------------------------------
Real hackers hack time ⌛

[~] The config file is expected to be at "/home/user/.rustscan.toml"
[~] Automatically increasing ulimit value to 5000.
Open 192.168.1.1:22
Open 192.168.1.1:80
Open 192.168.1.1:443
[~] Starting Script(s)
[>] Script to be run Some("nmap -vvv -p {{port}} {{ip}}")

Starting Nmap 7.91 ( https://nmap.org ) at 2023-01-01 12:00 UTC
...
```

## Real-World Use Cases

### 1. Quick Network Reconnaissance

```bash
rustscan -a 192.168.1.0/24 -b 500 --timeout 2000
```

Use case: Quickly discover all active hosts and open ports on a local network during initial network assessment.

### 2. Web Server Vulnerability Assessment

```bash
rustscan -a target.com -p 80,443,8080,8443 -- -sV -sC --script=vuln
```

Use case: Scan common web ports and run vulnerability scripts to identify potential security issues.

### 3. Stealth Scanning for Penetration Testing

```bash
rustscan -a target.com -b 10 --timeout 10000 -- -sS -T2
```

Use case: Slower, more careful scanning to reduce chances of detection during penetration testing.

### 4. Service Enumeration for All Open Ports

```bash
rustscan -a target.com --ulimit 5000 -- -sV -sC -A
```

Use case: Identify and fingerprint all services running on a target for thorough security assessment.

### 5. Regular Security Audits

```bash
rustscan -a internal-network.com -p 1-10000 --accessible > scan_results.txt
```

Use case: Scheduled scanning of internal infrastructure for unauthorized services or changes.

## Comparison with Other Tools

|Feature|RustScan|Nmap|Masscan|
|---|---|---|---|
|Speed|Very Fast|Moderate|Very Fast|
|Accuracy|Good|Excellent|Good|
|Resource Usage|Low|Moderate|Moderate|
|Detailed Analysis|Via Nmap|Built-in|Limited|
|Scripting|Limited|Extensive|Limited|
|Stealth Options|Limited|Extensive|Moderate|

## Best Practices

1. **Start with small batch sizes** on unknown networks to avoid overwhelming targets
2. **Increase timeouts** when scanning across the internet or high-latency networks
3. **Use the Nmap integration** for deeper inspection after discovering open ports
4. **Regularly update** RustScan to get the latest features and fixes
5. **Be mindful of legal implications** - always have permission to scan targets
6. **Save scan results** for future reference and comparison
7. **Use greppable or JSON output** for integration with other tools
8. **Monitor system resources** during large scans

## Configuration File Example

Create a file at `~/.rustscan.toml`:

```toml
# ~/.rustscan.toml

# General configuration
batch_size = 500
timeout = 2000
tries = 1
accessible = false
greppable = false

# Scan options
ports = "1-65535"
scan_order = "serial"
scan_type = "full"

# Output options
quiet = false
debug = false
```

## Related Tools to Pair with RustScan

- **Nmap**: For deeper analysis of discovered ports
- **Metasploit**: For exploitation of vulnerabilities
- **Wireshark**: For packet analysis during scanning
- **Burp Suite**: For web application testing after discovering web services
- **Nuclei**: For vulnerability scanning on discovered services

## Recent Developments (as of October 2024)

- Improved Docker support
- Better IPv6 handling
- Enhanced script execution capabilities
- Optimized scanning algorithms for reduced false positives

## Resources

- [Official GitHub Repository](https://github.com/RustScan/RustScan)
- [Documentation](https://github.com/RustScan/RustScan/wiki)
- [Issue Tracker](https://github.com/RustScan/RustScan/issues)