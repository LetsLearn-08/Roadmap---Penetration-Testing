# 🖥️ Windows 10 SOC Lab Setup

This subproject documents the setup of a Windows 10 virtual machine inside Oracle VirtualBox, configured for Security Operations Center (SOC) lab use. It includes installation steps, networking configuration, and post‑install security tooling — designed to help beginners replicate a detection‑focused environment.

---

## 🧰 Components
- **Windows 10 VM**: Installed from official ISO
- **VirtualBox**: Used for virtualization and resource allocation
- **SIEM‑VM**: Companion system for log collection and analysis

---

## 🌐 Networking
- Adapter 1: NAT (internet access for updates/tools)
- Adapter 2: Host‑only adapter (isolated lab traffic)
- IP range: `192.168.56.0/24`
- Verified connectivity between Windows VM and SIEM‑VM

---

## 🛠️ Installation
- Created VM with **6144 MB RAM**, **2 CPU cores**, **50 GB disk**
- Mounted `Windows.iso` on SATA Port 1
- Boot order set to **Optical → Hard Disk**
- Installed Windows 10 (Custom Install, new partition)
- Installed **VirtualBox Guest Additions** for clipboard, drag‑and‑drop, and display scaling

---

## 🔐 SOC Preparation
- Snapshot: `Win10_BaseInstall_ReadyForTools`
- Installed **Sysmon** with custom config
- Installed **Winlogbeat/NXLog** to forward logs to SIEM‑VM
- Created test users and simulated login events
- Installed visibility tools: Wireshark, Process Explorer, Autoruns

---

## 📚 Documentation
- [`windows-install.md`](markdown/windows-install.md): Step‑by‑step Windows VM setup
- [`guest-additions.md`](markdown/guest-additions.md): Installing VirtualBox Guest Additions
- [`soc-prep.md`](markdown/soc-prep.md): SOC hardening and tool setup
- [`status.md`](markdown/status.md): Current lab progress and next steps

---

## 📸 Proof Screenshot Checklist
- VM settings (RAM, CPU, storage, network)
- ISO mounted on SATA Port 1
- Boot order configuration
- Windows installer screen
- Post‑install desktop
- Guest Additions installer
- Snapshot confirmation

---

## 🎯 Goals
- Build a stable Windows environment for detection workflows
- Document setup for reproducibility and community sharing
- Lay the foundation for SIEM integration and detection engineering

---

## 🤝 Contribution
This lab is part of my cybersecurity learning journey. Feedback, suggestions, and collaboration are welcome!
