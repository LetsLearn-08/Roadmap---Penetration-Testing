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

## 🔍 Scan Modules

### 1. Basic Host Discovery
- **Command**: `nmap -sn <target-ip>`
- **Purpose**: Checks which hosts are up (ping scan)
- ### Step 1: Ping Sweep
Command: `nmap -sn 192.168.56.0/24`
Goal: Identify live hosts in subnet

---

### 2. Full Port Scan
- **Command**: `nmap -p- <target-ip>`
- **Purpose**: Scans all 65535 TCP ports
-  Command: `nmap -p- 192.168.56.101`
Goal: Scan all TCP ports

---

### 3. Service & Version Detection
- **Command**: `nmap -sV <target-ip>`
- **Purpose**: Identifies services and their versions
- Command: `nmap -sV 192.168.56.101`
Goal: Identify software versions

---

### 4. OS Detection
- **Command**: `nmap -O <target-ip>`
- **Purpose**: Guesses the OS based on TCP/IP fingerprinting
- Command: `sudo nmap -O 192.168.56.101`
Goal: Guess target OS

---

### 5. Aggressive Scan
- **Command**: `nmap -A <target-ip>`
- **Purpose**: Combines OS detection, version detection, script scan, and traceroute
- Command: `sudo nmap -A 192.168.56.101`
Goal: Deep scan with multiple techniques

---

### 6. NSE Script Scan
- **Command**: `nmap --script vuln <target-ip>`
- **Purpose**: Runs vulnerability detection scripts
### Step 1: List NSE Scripts
Command: `ls /usr/share/nmap/scripts/`
Goal: View available NSE scripts

### Step 2: Default NSE Scripts
Command: `nmap -sC 192.168.56.101`
Goal: Run default safe scripts

### Step 3: FTP Anonymous Login Check
Command: `nmap --script ftp-anon 192.168.56.101 -p 21`
Goal: Test for anonymous FTP access

### Step 4: Vulnerability Scan
Command: `nmap --script vuln 192.168.56.101`
Goal: Detect known vulnerabilities

### Step 5: Script Categories
Command: `nmap --script "default,safe" 192.168.56.101`
Goal: Run grouped scripts safely

### Step 6: Save Script Output
Command: `nmap --script vuln 192.168.56.101 -oN vuln_scan.txt`
Goal: Export scan results


---
## 🧪 Nmap Lab Module – Screenshot Documentation

This section contains organized screenshots from my Nmap lab module, executed in Kali Linux against Metasploitable2. Each image corresponds to a specific scan type or NSE script execution.

---

### 📁 Screenshot Index

| Scan Type               | Filename(s)                                                                 | Description                                  |
|------------------------|------------------------------------------------------------------------------|----------------------------------------------|
| Ping Sweep             | `ping-sweep.png`                                                             | Identifies live hosts in the target subnet   |
| OS Detection           | `os-det-1.png`, `os-det-2.png`                                               | Detects operating system of target machines  |
| Service Version Scan   | `svs-1.png`, `svs-2.png`, `svs-3.png`, `svs-4.png`                           | Reveals running services and versions        |
| Aggressive Scan        | `agg-scan-1.png`, `agg-scan-2.png`, `agg-scan-3.png`, `agg-scan-4.png`       | Combines multiple detection techniques       |
| Full Port Scan         | `full-portscan-1.png`, `full-portscan-2.png`, `full-portscan-3.png`, `full-portscan-4.png` | Scans all 65535 ports on the target          |
| Nmap Scan Series       | `nmap-scan-1.png`, `nmap-scan-2.png`, `nmap-scan-3.png`                      | General scan outputs for reference           |
| NSE Scripts            | `nse-script-1.1.png`, `nse-script-1.2.png`, `nse-script-1.3.png`, `nse-script-2.1.png`, `nse-script-2.2.png`, `nse-script-2.3.png`, `nse-script-2.4.png`, `nse-script-3.png`, `nse-script-4.1.png`, `nse-script-4.2.png`, `nse-script-5.1.png`, `nse-script-5.2.png`, `nse-script-6.png`, `nse-script-7.1.png`, `nse-script-7.2.png`, `nse-script-7.3.png`, `nse-script-7.4.png` | Executes specific NSE modules for deeper analysis |

---


All screenshots are stored in the [screenshots/nmap-lab](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/screenshots/nmap-lab) folder.


## 📝 Notes

- All scans were performed in a VirtualBox lab setup.
- Target machine: Metasploitable2
- Tool used: Nmap with various flags and NSE scripts
- Screenshots are organized by scan type and timestamp

---

## 📢 Connect

This repo is part of my cybersecurity learning journey.  
Follow me on [LinkedIn](https://www.linkedin.com/) for updates and lab walkthroughs.


---

### 📝 Notes

- All scans were executed in a controlled lab setup using VirtualBox.
- Screenshots are stored in `/screenshots/nmap-lab/` folder.
- This module is part of my ongoing penetration testing documentation project.


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
