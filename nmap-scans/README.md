# Nmap Overview and Usage Guide

## 🧠 What Is Nmap?
 Nmap (Network Mapper) is a free, open-source tool used for:
- Network discovery
- Security auditing
- Host and service detection
- OS fingerprinting
- Vulnerability scanning (via NSE scripts)

It’s widely used by ethical hackers, sysadmins, and pentesters to map networks and assess security.

## ⚙️ Core Capabilities
| Feature          | Description                                      |
|------------------|------------------------------------------------|
| Host Discovery   | Identifies live hosts on a network              |
| Port Scanning    | Finds open ports and services                    |
| Service Detection| Determines service name and version              |
| OS Detection     | Guesses the operating system and hardware       |
| Firewall Evasion | Uses stealth techniques to bypass filters        |
| NSE Scripting    | Runs custom scripts for vulnerability detection, brute force, etc. |
| Output Formats   | Supports plain text, XML, grepable, and interactive formats |

## 🔍 Scan Types & Flags

1. Ping Scan (Host Discovery)
```bash
nmap -sn <target>
``` 
Checks which hosts are up without scanning ports.

2.TCP Connect Scan
```bash
nmap -sT <target>
```
Uses full TCP connection — easy to detect, but reliable.

3.SYN Scan (Stealth Scan)
```bash
nmap -sS <target>
```
Sends SYN packets — fast and stealthy.

4.UDP Scan
```bash
nmap -sU <target>
```
Scans UDP ports — slower, but useful for DNS, SNMP, etc.

5.Service & Version Detection
```bash
nmap -sV <target>
```
Identifies running services and their versions.

6.OS Detection
```
nmap -O <target>
```
Guesses the OS based on TCP/IP stack behavior.

7.Aggressive Scan
```
nmap -A <target>
```
Combines OS detection, version detection, script scanning, and traceroute.

8.NSE Script Scan
```
nmap --script vuln <target>
```
Runs vulnerability detection scripts from the Nmap Scripting Engine.

## 🧾 Output Options

- -oN: Normal output
- -oX: XML output
- -oG: Grepable output
- -oA: All formats

Example:
```
nmap -sV -oA scan_results <target>
```

## 🧠 Best Practices

- Scan in a controlled lab (like your Kali + Metasploitable2 setup)
- Use -Pn to skip host discovery if ICMP is blocked
- Combine scans for deeper insight (e.g., -sS -sV -O)
- Document everything — flags, results, screenshots

# 🧪 Nmap Lab Practicals

This document outlines hands-on Nmap scanning techniques performed in a controlled lab setup using Kali Linux and Metasploitable2.

---

## ⚙️ Lab Setup

- **Host OS**: Kali Linux
- **Target VM**: Metasploitable2
- **Virtualization**: Oracle VirtualBox
- **Network**: Host-only adapter
- **Tools Used**: Nmap, Wireshark, Netcat

---


---

## 🔍 Scan Modules

### 1. Basic Host Discovery
- **Command**: `nmap -sn <target-ip>`
- **Purpose**: Checks which hosts are up (ping scan)
- **Save Screenshot**: `screenshots/basic-host-discovery.png`
- **Log Output**: `scans/basic/scan.md`

---

### 2. Full Port Scan
- **Command**: `nmap -p- <target-ip>`
- **Purpose**: Scans all 65535 TCP ports
- **Save Screenshot**: `screenshots/full-port-scan.png`
- **Log Output**: `scans/basic/scan.md`

---

### 3. Service & Version Detection
- **Command**: `nmap -sV <target-ip>`
- **Purpose**: Identifies services and their versions
- **Save Screenshot**: `screenshots/service-version.png`
- **Log Output**: `scans/service-version/scan.md`

---

### 4. OS Detection
- **Command**: `nmap -O <target-ip>`
- **Purpose**: Guesses the OS based on TCP/IP fingerprinting
- **Save Screenshot**: `screenshots/os-detection.png`
- **Log Output**: `scans/OS-detection/scan.md`

---

### 5. Aggressive Scan
- **Command**: `nmap -A <target-ip>`
- **Purpose**: Combines OS detection, version detection, script scan, and traceroute
- **Save Screenshot**: `screenshots/aggressive-scan.png`
- **Log Output**: `scans/aggressive/scan.md`

---

### 6. NSE Script Scan
- **Command**: `nmap --script vuln <target-ip>`
- **Purpose**: Runs vulnerability detection scripts
- **Save Screenshot**: `screenshots/nse-vuln-scan.png`
- **Log Output**: `scans/custom-scripts/scan.md`

---

## ✅ Progress Tracker

Use `status.md` to track:
- ✅ Completed scans
- 🛠️ Pending modules
- 🐞 Errors encountered
- 📸 Screenshots uploaded

---

## 📎 Notes


- [🧾 Scan Cheatsheet](notes/scan-cheatsheet.md): Quick reference for Nmap flags and examples
- [🐞 Troubleshooting Guide](notes/troubleshooting.md): Common issues and fixes during scanning


---

## 🔗 Related Projects

- [`netcat-lab`](../netcat-lab): Netcat modules including port scanning, banner grabbing, file transfer, and chat simulation




