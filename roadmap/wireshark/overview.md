# 🦈 Wireshark Learning Lab

## 📖 Overview
Wireshark is a powerful **network protocol analyzer** that lets you capture and inspect packets in real time.  
This repository is designed for **beginners** learning networking, cybersecurity, and packet analysis step by step.

---

## 📂 Repository Structure

### 🧪 Labs (`/labs`)
Hands-on, practical Wireshark analysis tasks:

- [ping-test.md](labs/ping-test.md) → ICMP echo request/reply analysis  
- [web-browsing.md](labs/web-browsing.md) → HTTP GET/POST inspection  
- [arp-resolution.md](labs/arp-resolution.md) → ARP discovery & MAC mapping  
- [suspicious-traffic.md](labs/suspicious-traffic.md) → Detecting scans & anomalies  

---

### 📘 Cheatsheets (`/cheatsheets`)
Quick references you’ll use daily:

- [filters.md](cheatsheets/filters.md) → Capture & display filter examples  
- [shortcuts.md](cheatsheets/shortcuts.md) → Productivity shortcuts & workflow tips  

---

### 📚 Units (`/units`)
Structured learning modules for a complete Wireshark journey:

- [unit-1-installation.md](units/unit-1-installation.md) → Installation & interface basics  
- [unit-2-filters-streams.md](units/unit-2-filters-streams.md) → Filters & stream following  
- [unit-3-protocols.md](units/unit-3-protocols.md) → Deep dives: DNS, HTTP, ARP, ICMP  
- [unit-4-security.md](units/unit-4-security.md) → Detecting scans & suspicious traffic  
- [unit-5-advanced.md](units/unit-5-advanced.md) → Advanced analysis: TLS, reassembly, exports  

---

## 🚀 Getting Started

### 🛠 Installation

#### Linux (Kali / Ubuntu)
```bash
sudo apt update
sudo apt install wireshark
sudo usermod -aG wireshark $USER
```

- Log out and back in for group changes to take effect.

#### Windows / macOS
 
 -   Download the installer from wireshark.org.
 - Follow the setup wizard (on Windows, install WinPcap/Npcap when prompted).
 - Launch Wireshark from the Start Menu or Applications folder.

## ▶️ Launching Wireshark

- Open Wireshark.
- Select an interface (Ethernet, Wi-Fi, or Loopback).
- Click the blue shark fin 🦈 to start capturing.
- Stop capture with the red square button when done.

## 🔍 Core Concepts

- Capture Filters (before capture):
   - tcp port 80 → only capture HTTP traffic
   - host 192.168.1.10 → only capture traffic to/from a host
- Display Filters (after capture):
  - http → show HTTP packets
  - ip.addr == 192.168.1.1 → show traffic involving a specific IP
- Follow Streams
  - Right-click a packet → Follow TCP Stream → view full conversation
- Color Coding
  - Wireshark highlights protocols (TCP, UDP, ICMP) with different colors for quick recognition

## 🎯 Lab Exercises

- [Ping Test](./labs/ping-test.md) → ICMP traffic analysis  
- [Web Browsing](./labs/web-browsing.md) → Inspect HTTP requests/responses  
- [ARP Resolution](./labs/arp-resolution.md) → Observe ARP traffic  
- [Suspicious Traffic](./labs/suspicious-traffic.md) → Detect port scans  

---

## 📚 Learning Roadmap

- [Unit 1: Installation & Interface Basics](./units/unit-1-installation.md)  
- [Unit 2: Filters & Streams](./units/unit-2-filters-streams.md)  
- [Unit 3: Protocol Deep Dives](./units/unit-3-protocols.md)  
- [Unit 4: Security Use Cases](./units/unit-4-security.md)  
- [Unit 5: Advanced Analysis](./units/unit-5-advanced.md)  

   
---

## 🛡️ Ethics Reminder

- Wireshark is a powerful forensic tool. Use it responsibly:
- Capture only traffic you’re authorized to analyze.
- Avoid sniffing networks without consent.
- Apply your skills in labs, classrooms, or authorized environments.

- ---

## 📝 Notes

- All captures were performed in a **controlled lab setup** (VirtualBox).  
- Target machine: **Metasploitable2** and test hosts in the same network.  
- Tool used: **Wireshark** with various filters and stream analysis.  
- Screenshots are organized by **protocol type** and **timestamp** in [`/screenshots/wireshark-lab/`](./screenshots/wireshark-lab/).  

---

## 📢 Connect

This repo is part of my **cybersecurity learning journey**.  
Follow me on [LinkedIn](www.linkedin.com/in/tanuja-reddy-03aa7b38a) for updates, lab walkthroughs, and progress logs.

---

## ✅ Progress Tracker

Use [`status.md`](./status.md) to track:

- ✅ Completed labs (Ping, HTTP, ARP, Suspicious Traffic)  
- 🛠️ Pending modules (Advanced TLS, Export Objects)  
- 🐞 Errors encountered during captures or filter usage  
- 📸 Screenshots uploaded for documentation  

---

## 🔗 Related Modules

- [Nmap Lab](../nmap/README.md) → Scan IPs and ports discovered in Wireshark  
- [theHarvester Lab](../theHarvester/README.md) → OSINT reconnaissance before packet analysis  
- [Netcat Lab](../netcat/README.md) → Test open ports and interact with services  

---

## ⚖️ Ethical Reminder

All captures are performed in a **controlled lab environment**.  
Never sniff or analyze traffic on networks you don’t own or have explicit permission to test.



### Wireshark: Your microscope for the internet
