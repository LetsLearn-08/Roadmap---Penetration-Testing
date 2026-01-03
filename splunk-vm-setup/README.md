# 📊 Splunk SIEM Lab Setup

This subproject documents the setup of a Splunk virtual machine inside Oracle VirtualBox, configured for Security Operations Center (SOC) lab use. It includes installation steps, networking configuration, and post‑install integration — designed to help beginners replicate a log analysis and detection environment.

---

## 🧰 Components
- **Splunk VM**: Installed from official Splunk Enterprise package
- **VirtualBox**: Used for virtualization and resource allocation
- **Windows 10 SOC VM**: Forwarding logs to Splunk for analysis
- **Kali + Metasploitable2**: Generating attack traffic for detection

---

## 🌐 Networking
- Adapter 1: NAT (internet access for updates/tools)
- Adapter 2: Host‑only adapter (isolated lab traffic)
- IP range: `192.168.56.0/24`
- Verified connectivity between Splunk VM and Windows SOC VM

---

## 🛠️ Installation
- Created VM with **4096 MB RAM**, **2 CPU cores**, **40 GB disk**
- Installed base OS (Ubuntu Server recommended)
- Downloaded and installed **Splunk Enterprise** from official site
- Configured Splunk to run as a service
- Enabled web interface on port `8000`

---

## 🔐 SOC Preparation
- Snapshot: `Splunk_BaseInstall_ReadyForIntegration`
- Configured **inputs.conf** to receive logs from Windows SOC VM
- Set up **Winlogbeat/NXLog** on Windows to forward logs
- Created initial dashboards for event monitoring
- Configured alerts for suspicious login attempts and process creation

---

## 📚 Documentation
- [`splunk-install.md`](markdown/splunk-install.md): Step‑by‑step Splunk VM setup
- [`splunk-integration.md`](markdown/splunk-integration.md): Connecting Windows SOC VM logs
- [`splunk-dashboards.md`](markdown/splunk-dashboards.md): Creating dashboards and alerts
- [`status.md`](markdown/status.md): Current lab progress and next steps

---

## 📸 Proof Screenshot Checklist
- VM settings (RAM, CPU, storage, network)
- Splunk installation terminal output
- Splunk web login screen (`http://<vm-ip>:8000`)
- Forwarded logs visible in Splunk
- Dashboard with events/alerts
- Snapshot confirmation

---

## 🎯 Goals
- Build a Splunk SIEM environment for log ingestion and analysis
- Document integration with Windows SOC VM
- Simulate attack traffic from Kali/Metasploitable and detect in Splunk
- Share reproducible setup for community learning

---

## 🤝 Contribution
This lab is part of my cybersecurity learning journey. Feedback, suggestions, and collaboration are welcome!
