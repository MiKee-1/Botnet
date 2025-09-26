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

---

## Educational Value

By studying and experimenting with this code in a **sandboxed environment**, students and researchers can:

* Explore how RATs implement encrypted communications.
* Understand attacker tactics such as persistence, data theft, and lateral movement.
* Learn how to recognize malicious behavior on networks and endpoints.
* Practice writing defensive rules (IDS signatures, log monitoring, behavioral detection).
* Identify insecure coding practices (hardcoded keys, missing authentication, unsafe command handling).

---

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

4. **Run inside the lab only**

   * Start the server (`python server.py`).
   * Connect test clients (VMs or simulated agents).
   * Experiment only with machines you fully control.

---

#
## Safe Testing Guidelines

* Always run in a **sandbox** or isolated VM environment.
* Never connect client code to production or personal systems.
* Monitor network traffic with tools like **Wireshark** or **tcpdump** to analyze encrypted C2.
* Use endpoint monitoring tools to detect file writes, privilege checks, and suspicious processes.
* Document your observations as if performing a **malware analysis report**.

---

## Research Applications

* **Cybersecurity education**: Teaching how RATs function internally.
* **Red vs. Blue exercises**: Simulating attacker/defender scenarios in controlled labs.
* **Malware reverse-engineering**: Comparing this open code to real-world RAT families.
* **Defensive testing**: Developing detection rules for IDS/IPS, SIEMs, and EDR systems.

---

## Removed for Safety

If you plan to adapt this project for teaching, we recommend disabling or removing these parts:

* Data exfiltration (credentials, clipboard).
* Denial-of-service routines.
* Self-spreading mechanisms.
* Anti-forensics commands.

Instead, replace them with **harmless placeholders** (e.g., fake credential data, mock clipboard text, dummy network scans).

---

## Legal Notice
* Legal: Unauthorized access, distribution, or deployment of this code is prohibited by law. Use only in **ethical, academic, or defensive security contexts**.
