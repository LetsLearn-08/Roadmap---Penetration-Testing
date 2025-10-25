> 📄 View-only content. Licensed under terms in [LICENSE-NOTES.md](../LICENSE-NOTES.md).


# 🧠 Nmap Scanning Techniques Overview

Nmap (Network Mapper) is a powerful tool for network reconnaissance and vulnerability assessment. It supports multiple scanning modes, each suited for different goals.

📄 **Related Files**  
- 👉 [Lab Cheatsheet](./lab-cheatsheet.md)  
- 🖼️ All screenshots are stored in the [screenshots/nmap-lab](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/screenshots/nmap-lab) folder.

---

## 🔍 1. Host Discovery  
Used to identify live hosts on a network.

- **Ping Scan** (`-sn`) — checks which hosts are up without scanning ports.  
```bash
nmap -sn 192.168.1.0/24
```

- **ARP Scan** (`-PR`) — effective on local Ethernet networks.  
```bash
nmap -PR 192.168.1.0/24
```

- **ICMP types** (`-PE`, `-PP`, `-PM`) — Echo, Timestamp, Netmask requests.  
```bash
nmap -sn -PE -PP -PM 10.0.0.0/24
```

---

## 🔓 2. Port Scanning  
Used to identify open ports and services.

| Technique            | Flag              | Description                                       |
|----------------------|------------------:|---------------------------------------------------|
| TCP Connect Scan     | `-sT`             | Full TCP handshake. Reliable but noisy.          |
| SYN Scan             | `-sS`             | Stealthy half-open scan. Fast and popular.       |
| UDP Scan             | `-sU`             | Scans UDP ports. Slower and less reliable.       |
| ACK Scan             | `-sA`             | Maps firewall rules; doesn't show open ports.    |
| FIN/Xmas/Null Scans  | `-sF`, `-sX`, `-sN`| Bypass firewalls using unusual TCP flags.        |

Example usage:
```bash
nmap -sT 203.0.113.5
nmap -sS -T4 203.0.113.5
nmap -sS -p 1-1000 203.0.113.5
nmap -sU -p 53,67,68,123 203.0.113.5
nmap -sA 203.0.113.5
nmap -sF 203.0.113.5
```

---

## 🧬 3. Service & Version Detection  
Detect services and versions running on open ports.

```bash
nmap -sV 203.0.113.5
nmap -sS -sV -p 22,80,443 203.0.113.5
```

---

## 🧪 4. OS Detection  
Uses TCP/IP stack fingerprinting to guess the target OS.

```bash
sudo nmap -O 203.0.113.5
sudo nmap -A 203.0.113.5
```

---

## 🧠 5. Script Scanning (NSE)  
Nmap Scripting Engine runs scripts for discovery, vulnerability checks, brute force, and more.

- **Default scripts**: `-sC`  
- **Specific scripts**: `--script=<name>`

Examples:
```bash
nmap -sC 203.0.113.5
nmap --script=vuln 203.0.113.5
nmap --script=http-enum,ssl-heartbleed 203.0.113.5
nmap -sS -sV --script=vuln -p 80,443 203.0.113.5
```

## 📁 Output Formats

Nmap can save results in multiple formats:

- `-oN <file>`: Normal human-readable output  
- `-oX <file>`: XML output (good for parsers)  
- `-oG <file>`: Grepable output (easy to filter)  
- `-oA <basename>`: Save in all formats (`basename.nmap`, `basename.xml`, `basename.gnmap`)

Example:
```bash
sudo nmap -sS -sV -O -p- -T4 -oA scan-results 203.0.113.5
```

## Advanced port selection & timing :
```markdown
## ⏱ Timing, Ports & Performance

- `-p-` : scan all TCP ports (1–65535)  
- `--top-ports <n>` : scan the most common `n` ports  
- `-T0` .. `-T5` : timing templates (T3 safe, T4 aggressive)

Tuning examples:
```bash
# Scan top 100 ports fast
nmap --top-ports 100 -T4 203.0.113.5

# Scan all ports with moderate timing
sudo nmap -sS -p- -T3 203.0.113.5
```

## 
**4) Evasion & special scans (copy-paste):**
```markdown
## 🛡 Firewall Evasion & Special Scans

Use with caution — some techniques are noisy or suspicious.

- Fragment packets: `-f`  
- Decoys: `-D decoy1,decoy2,ME`  
- Source port / spoofing: `-g <port>` / `-S <addr>` (advanced)  
- Idle/Zombie scan: `-sI <zombie_host>`  
- Data/payload size: `--data-length <n>`

Example:
```bash
# Fragmented SYN scan with decoys
sudo nmap -sS -f -D decoy1,decoy2,ME 203.0.113.5
```


**Script Help & Path**
```bash
nmap --script-help http-enum
# Script directory (Linux):
# /usr/share/nmap/scripts/
```

---

## ✅ Quick Cheat-sheet
```bash
# Fast ping sweep
nmap -sn 192.168.1.0/24

# SYN scan with top 1000 ports
nmap -sS -T4 192.168.1.0/24

# Full scan with OS, version, and scripts
sudo nmap -A -sV -O -p- -T4 -oA target-full 203.0.113.5

# Vulnerability detection
nmap -sV --script=vuln -p 80,443 203.0.113.5
```

---

## ⚠️ Legal & Ethical Reminder  
Only scan networks and hosts you **own** or have **explicit permission** to test. Unauthorized scanning is illegal in many jurisdictions.

## Every open port is a story waiting to be told. Nmap is your narrator.

 # STAY TUNED TILL NEXT WEEK..@LetsLearn-08
