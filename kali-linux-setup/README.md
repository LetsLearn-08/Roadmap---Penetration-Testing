# Kali Linux Setup Lab

This subproject documents the setup of a penetration testing lab using Kali Linux and Metasploitable2 inside Oracle VirtualBox. It includes networking configuration, installation steps, and troubleshooting notes — all designed to help beginners replicate the lab environment.

## 🧰 Components
- **Kali Linux VM**: Installed from official ISO
- **Metasploitable2 VM**: Vulnerable target for testing
- **VirtualBox**: Used for virtualization and network setup

## 🌐 Networking
- Host-only adapter configured for isolated lab traffic
- IP range: `192.168.56.0/24`
- Verified connectivity between Kali and Metasploitable2

## 📚 Documentation
- [`kali-install.md`](markdown/kali-install.md): Step-by-step Kali VM setup
- [`host-only-networking.md`](markdown/host-only-networking.md): Networking config guide
- [`troubleshooting.md`](markdown/troubleshooting.md): Common setup issues and fixes
-  [`status.md`](markdown/status.md): Current lab progress and next steps

## 🎯 Goals
- Build a stable lab for scanning, enumeration, and exploitation
- Document setup for future reuse and community sharing
- Lay the foundation for future subprojects (Nmap, Wireshark, Burp Suite, etc.)

## 🤝 Contribution
This lab is part of my cybersecurity learning journey. Feedback, suggestions, and collaboration are welcome!

