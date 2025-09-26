# README — BOTNET

## ⚠️ Disclaimer

This repository contains code that demonstrates functionalities commonly found in **Remote Access Trojans (RATs)**.
It is provided **solely for academic study, malware analysis training, and defensive cybersecurity research.**

Running this code against systems without explicit permission is **illegal and unethical**. The authors and contributors do **not endorse malicious use** of this project.

---

## Overview

This project showcases how a **Command-and-Control (C2) server** can manage multiple remote clients using encrypted communication. It provides insight into the techniques attackers use to build RATs, including:

* Encrypted traffic with symmetric cryptography (AES).
* Session management for multiple clients.
* Remote shell execution.
* File transfer and data exfiltration.
* Attack and persistence mechanisms (as seen in real malware families).

From a **defensive perspective**, this code is useful for understanding:

* The structure of RAT communications.
* How data exfiltration and remote execution typically occur.
* Indicators of compromise (IoCs) that defenders can monitor in real environments.

---

## Features (for educational analysis)

> These features are included in the code for research purposes. They should never be deployed outside a controlled lab.

* **Encryption:** Communication secured with AES (CBC mode) and Base64 encoding.
* **Multi-session management:** Ability to accept and interact with multiple clients.
* **Remote shell:** Execution of system commands on connected hosts.
* **File operations:** Upload and download between server and clients.
* **Data extraction examples:** Clipboard content, system/network information, and stored credentials.
* **Attack primitives (unsafe in production):** SYN flooding, log cleaning, directory encryption.
* **Spreading techniques:** Simulated routines for propagation in a local network.


## Installation (Safe Setup in a Lab Environment)

1. **Prepare an isolated environment**

   * Use virtual machines (VMware, VirtualBox, or QEMU).
   * Ensure the lab is not connected to the internet or production networks.

2. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/educational-rat-analysis.git
   cd educational-rat-analysis
   ```

3. **Set up Python environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # Linux / macOS
   venv\Scripts\activate      # Windows
   pip install -r requirements.txt
   ```
---

## Safe Testing Guidelines

* Always run in a **sandbox** or isolated VM environment.
* Never connect client code to production or personal systems.
* Monitor network traffic with tools like **Wireshark** or **tcpdump** to analyze encrypted C2.
* Use endpoint monitoring tools to detect file writes, privilege checks, and suspicious processes.
* Document your observations as if performing a **malware analysis report**.

## Removed for Safety

If you plan to adapt this project for teaching, we recommend disabling or removing these parts:

* Data exfiltration (credentials, clipboard).
* Denial-of-service routines.
* Self-spreading mechanisms.
* Anti-forensics commands.

Instead, replace them with **harmless placeholders** (e.g., fake credential data, mock clipboard text, dummy network scans).

---

## Legal Disclaimer

This software is provided for:
- Educational purposes
- Authorized penetration testing
- Security research
- Red team exercises

**You must have explicit permission** before deploying this tool on any system. The authors are not responsible for misuse of this software.

### Surveillance Capabilities
- Keylogging
- Clipboard monitoring
- System information gathering
- Network information collection
- Browser password extraction

### Network Operations
- Port scanning
- Network host discovery
- SYN flood attacks (DDoS)
- Lateral movement techniques

### Security Evasion
- Polymorphic code execution
- Anti-forensics (log deletion)
- Sandbox detection
- Persistence mechanisms

### Encryption
- AES-256 CBC encryption for all communications
- File and directory encryption/decryption
- String obfuscation

## Architecture

### Client (client.py)
- Connects to C2 server
- Executes commands received from server
- Implements various surveillance and attack modules
- Includes evasion techniques

### Server (server.py)
- Listens for client connections
- Provides command interface
- Manages multiple concurrent connections
- Encrypted communication channel

### Configuration

1. **Update Server IP** in client.py:
```python
server('192.168.1.102', 4444)  # Change to your server IP
```

2. **AES Encryption Keys** (both client and server):
```python
AES_KEY = b'ThisIsA32ByteIVForAES256Encrypt!'
AES_IV = b'ThisIsA16ByteIV!'
```

### Usage

1. **Start the Server**:
```bash
python server.py
```

2. **Deploy Client** on target systems
3. **Connect from Server** using the interactive menu

## Command Reference

### Center Commands
- `targets` - List connected clients
- `session [number]` - Connect to specific client
- `sendall [command]` - Send command to all clients
- `quit` - Exit server
- `clear` - Clear screen
- `help` - Show command help

### Client Shell Commands
- `exit` - Return to center
- `check_priv` - Check privileges
- `download/upload` - File transfer
- `start_keylogger/stop_keylogger` - Keylogging
- `encrypt_dir/decrypt_dir` - File encryption
- `steal_creds` - Extract browser passwords
- `port_scan` - Network scanning
- `spread` - Lateral movement
- `anti_forensics` - Delete logs

## Security Features

### Communication Security
- All traffic encrypted with AES-256-CBC
- Base64 encoding for data transmission
- JSON format for command structure

### Evasion Techniques
- Polymorphic code generation
- Sandbox environment detection
- Anti-debugging measures
- Persistence through startup and registry

## Important Notes

### Detection Risks
This tool may be detected by:
- Antivirus software
- EDR solutions
- Network monitoring tools
- Behavioral analysis systems

### Operational Security
- Change default encryption keys
- Use secure communication channels
- Implement proper access controls
- Monitor for unauthorized use

## Educational Value

This project demonstrates:
- Remote administration techniques
- Network security concepts
- Cryptography implementation
- System programming
- Ethical hacking methodologies

## Learning Objectives

- Understand RAT architecture
- Learn about persistence mechanisms
- Study encryption in malware
- Analyze detection evasion techniques
- Explore ethical hacking tools

## Contributing

This is an educational project. Contributions should focus on:
- Improving documentation
- Enhancing educational value
- Adding security features
- Bug fixes and optimization



## For educational purposes only. Users are responsible for complying with all applicable laws.
