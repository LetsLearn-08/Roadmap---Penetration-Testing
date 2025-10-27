

# Metasploitable2 Subproject 


**Purpose:** 
A step-by-step, professional, and beginner-friendly guide that also includes practical intermediate/pleasantly-advanced topics useful for a pentester-in-training. This version avoids deep core research-level detail but covers the essential advanced techniques you’ll actually use in labs and initial engagements.

---

## 📘 Project Overview

* Discover hosts and services using Nmap.
* Interpret scan results and prioritize next steps.
* Document, save, and reuse scan outputs for reporting and further testing.

---


## ⚠️ Safety & Legal Reminder

Only scan machines you own or have explicit permission to test. Use this guide **only** inside an isolated lab. Snapshot VMs before exploitation.

---


## 🎯 Project Goals

- Learn how to use Nmap for full, targeted, and scripted scans.
- Practice safe enumeration and vulnerability discovery in an isolated lab.
- Document scan results with markdown summaries and screenshots.
- Build reusable templates and scripts for future labs.

---

## 🧰 Tools Used

- Kali Linux (Attacker VM)
- Metasploitable2 (Target VM)
- Nmap (Network scanner)
- Markdown (Documentation)
- Bash (Automation scripts)

## Workflow 

Follow this for each target IP — includes intermediate steps.

1. **Connectivity check:** `ping <target-ip>`
2. **Mass discovery (optional, large nets):** `masscan -p1-65535 --rate=1000 <target-ip-range> -oL masscan_out.txt` (use only in lab)
3. **Focused TCP discovery:** `nmap -sS -sV -p 1-1024 <target-ip> -oN outputs/first_tcp_scan.txt`
4. **Full TCP comprehensive:** `nmap -p- -sV -T4 <target-ip> -oA outputs/full_tcp_scan`
5. **UDP quick checks:** `nmap -sU -p 53,67,68,69,123,161 <target-ip> -oN outputs/udp_quick.txt`
6. **Safe NSE enumeration:** `nmap -sV -sC -p 1-1024 <target-ip> -oN outputs/safe_enum.txt`
7. **Targeted vuln NSE:** `nmap --script "vuln" -p 21,80,445 <target-ip> -oN outputs/vuln_scripts.txt` (lab only)
8. **OS detection & traceroute:** `nmap -O --traceroute <target-ip> -oN outputs/os_traceroute.txt`

---


## 🧪 Scan Types Covered

- Full TCP port scan
- Targeted service scans (FTP, SSH, HTTP)
- NSE script scans (discovery, vuln, enum)
- OS detection and service versioning
- Optional UDP enumeration (lab-safe scope)

---

## 📦 Advanced Guide 

See [`Nmap Scan Types — Metasploitable2 Subproject`](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/blob/main/nmap-scans/README.md?plain=1) for a conceptual guide that explains:
- Scan workflows and reporting structure
- NSE script categories and usage
- Parsing and automation concepts
- Evasion techniques (lab-only)
- What to record after each scan

---

# 🧪 Lab Module: Nmap Scanning Metasploitable2

## 🎯 Objective

Perform and document multiple Nmap scans against Metasploitable2 to identify open ports, services, and potential vulnerabilities. Learn how to organize findings, use NSE scripts safely, and prepare for exploitation.

---

## 🧰 Lab Requirements

| Component        | Description                                    |
| ---------------- | ---------------------------------------------- |
| Attacker Machine | Kali Linux (VirtualBox or native)              |
| Target Machine   | Metasploitable2 VM                             |
| Network Setup    | Host-only or NAT network (ensure connectivity) |
| Tools            | Nmap, Bash, Markdown editor                    |

---

## 🧭 Lab Steps

1. 🔗 **Connectivity Check**
 ```
   ping <target-ip>
traceroute <target-ip>
```
   * Confirm Metasploitable2 is reachable from Kali.
   * Log the method used (ping, traceroute, etc.).

3. 🚀 **Fast Discovery Scan**
```
nmap -sS -sV <target-ip> -oN fast-scan.txt
```
   * Scan top 1000 TCP ports.
   * Save output and screenshot.
   * Note key services discovered.

5. 🧱 **Full TCP Scan**
```
nmap -p- -sV <target-ip> -oN full-scan.txt
```
   * Scan all 65,535 TCP ports.
   * Save output and screenshot.
   * Compare with fast scan results.

6. 🌐 **Targeted Service Scans**
FTP (Port 21)
```
nmap -p 21 -sV <target-ip> -oN ftp-scan.txt
```
SSH (Port 22)
```
nmap -p 22 -sV <target-ip> -oN ssh-scan.txt
```
HTTP (Port 80)
```
nmap -p 80 -sV <target-ip> -oN http-scan.txt
```
SMB (Port 445)
```
nmap -p 445 -sV <target-ip> -oN smb-scan.txt
```
   * Scan FTP (21), SSH (22), HTTP (80), SMB (445).
   
7. 🧠 **NSE Script Scans**
FTP Vulnerability Scan
```
nmap --script ftp-vuln* -p 21 <target-ip> -oN ftp-vuln.txt
```
HTTP Enumeration
```
nmap --script http-enum -p 80 <target-ip> -oN http-enum.txt
```
SMB Enumeration
```
nmap --script smb-enum* -p 445 <target-ip> -oN smb-enum.txt
```
   * Run safe discovery scripts first.
   * Then run targeted vulnerability scripts (e.g., ftp-vuln*, http-enum).
  

8. 🧪 **OS Detection & Mapping**
 ```
nmap -O --traceroute <target-ip> -oN os-detect.txt
```
   * Run OS detection and traceroute.
   * Note guesses and network path info.

9. 📝 **Document Findings**

   * Use `findings-summary.md` to log:

     * Open ports
     * Service versions
     * NSE highlights
     * Manual verification (e.g., anonymous FTP login)
     * Suggested next steps

---

## 📦 Deliverables

* Structured folder with scan outputs and screenshots
* Completed `findings-summary.md`
* Filled `nse-template.md` for each script used
* Optional: `scan.sh` script with your commands

---

## 🧠 Learning Outcomes

* Understand Nmap scan types and when to use them
* Safely use NSE scripts for enumeration
* Organize and report findings like a junior pentester
* Prepare for exploitation based on scan results

---

## 📊 Metasploitable2 — Nmap Findings Summary

This file summarizes key findings from multiple Nmap scans performed against the Metasploitable2 VM. Each section includes open ports, detected services, NSE script results, and manual verification notes.

---

### 🖥️ Target Info

- **IP Address**: 192.168.56.101
- **Scan Date**: 2025-10-26
- **Attacker Machine**: Kali Linux
- **Target Machine**: Metasploitable2

---

### 🔍 Full TCP Scan

- **Command**: `nmap -p- -sV 192.168.56.101 -oN full-scan.txt`
- **Open Ports & Services**:
  | Port | Service       | Version             |
  |------|---------------|---------------------|
  | 21   | FTP           | vsftpd 2.3.4        |
  | 22   | SSH           | OpenSSH 4.7p1       |
  | 23   | Telnet        | Linux telnetd       |
  | 25   | SMTP          | Postfix smtpd       |
  | 80   | HTTP          | Apache 2.2.8        |
  | 139  | NetBIOS       | Samba smbd 3.x      |
  | 445  | SMB           | Samba smbd 3.x      |
  | 3306 | MySQL         | MySQL 5.0.51a       |
  | 5432 | PostgreSQL    | PostgreSQL 8.3.0    |
  | 8009 | Apache JServ  | ajp13               |
  | 8180 | HTTP          | Apache Tomcat/Coyote|

---

## 🎯 Targeted Scans

### FTP (Port 21)
- **Service**: vsftpd 2.3.4
- **Vulnerability**: Backdoor confirmed via NSE and Netcat shell
- **Exploit Available**: `exploit/unix/ftp/vsftpd_234_backdoor`

### HTTP (Port 80)
- **Service**: Apache 2.2.8
- **Vulnerability**: Directory listing enabled, outdated version
- **Manual Check**: Browsed `/manual/` and `/icons/` directories

### SMB (Port 445)
- **Service**: Samba smbd 3.x
- **Vulnerability**: Enumerated shares and users via NSE
- **Manual Check**: Connected with `smbclient` (anonymous login allowed)

---

## 🧠 NSE Script Results

### ftp-vuln-backdoor
- **Result**: Backdoor detected
- **Manual Verification**: Shell access confirmed via Netcat

### http-enum
- **Result**: Multiple directories exposed
- **Manual Verification**: Accessible via browser

### smb-enum-shares
- **Result**: Shared folders listed
- **Manual Verification**: Accessed `tmp` share anonymously

---

## 🧪 OS Detection

- **Command**: `nmap -O --traceroute 192.168.56.101 -oN os-detect.txt`
- **Result**: OS guessed as Linux 2.6.X
- **Traceroute**: 1 hop, direct connection

---

## 📸 Screenshot References

| Filename                  | Description                          |
|---------------------------|--------------------------------------|
| full-scan-ports.png       | All open ports from full scan        |
| ftp-vuln-backdoor.png     | NSE output showing FTP backdoor      |
| http-enum.png             | NSE output showing HTTP directories  |
| smb-enum-shares.png       | Samba shares listed via NSE          |
| netcat-shell.png          | Shell access via FTP backdoor        |

---

## 🧠 NSE Script Report — FTP Service

### 🖥️ Target Information
- **IP Address**: 192.168.56.101
- **Port**: 21
- **Service**: vsftpd 2.3.4

---

### 📜 Script Details
- **Script Name**: ftp-vuln-backdoor
- **Category**: vuln
- **Arguments Used**: None
- **Command Run**: `nmap --script ftp-vuln-backdoor -p 21 192.168.56.101 -oN ftp-vuln.txt`

---

### 📂 Output Summary
- **Key Findings**:
  - The script detected a backdoor vulnerability in vsftpd 2.3.4.
  - It reported that a malicious version of vsftpd allows remote shell access via a crafted username.
  - No CVE listed, but this is a known exploit used in beginner labs.
- **Script Behavior Notes**:
  - Script executed successfully with no errors.
  - Output was concise and clearly flagged the vulnerability.

---

### 🔍 Manual Verification
- **Follow-up Tests**:
  - Attempted to connect via Netcat using crafted username `user:)`.
- **Result**:
  - Connection succeeded and spawned a shell — vulnerability confirmed.

---

### 🔍 Full Scan Summary

- **Open Ports**: 21, 22, 23, 25, 80, 139, 445, 3306, 5432, 8009, 8180
- **Detected Services**:
  - FTP (vsftpd 2.3.4)
  - SSH (OpenSSH 4.7p1)
  - Telnet (Linux telnetd)
  - SMTP (Postfix smtpd)
  - HTTP (Apache 2.2.8)
  - MySQL (5.0.51a)
  - PostgreSQL (8.3.0)
- **Notes**: Many services are outdated and vulnerable — ideal for testing exploits.

---

### 🎯 Targeted Scan Highlights

#### FTP (Port 21)
- **Service**: vsftpd 2.3.4
- **Vulnerability**: Backdoor exploit available

#### SSH (Port 22)
- **Service**: OpenSSH 4.7p1
- **Vulnerability**: Weak configuration, brute-force possible

#### HTTP (Port 80)
- **Service**: Apache 2.2.8
- **Vulnerability**: Directory listing enabled, outdated version

---

### 🧠 NSE Script Results

#### FTP Vuln Scan
- **Result**: vsftpd backdoor confirmed
- **Exploit**: Metasploit module available

#### HTTP Enum
- **Result**: Multiple directories exposed
- **Notes**: Useful for web enumeration and brute-forcing

---


## ⚠️ Legal Reminder

Only scan machines you own or have permission to test. This project is for educational use in isolated labs only.

---

## Happy scanning, documenting, and leveling up your pentesting skills! 💻🔍

