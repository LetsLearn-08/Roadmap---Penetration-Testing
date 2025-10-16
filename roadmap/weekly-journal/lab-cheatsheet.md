# Lab Cheatsheet — Nmap Quick Reference

**Filename:** `lab-cheatsheet.md`  
**Purpose:** Short, copy-paste friendly commands and notes for lab exercises.

---

## 🔑 Quick Tips
- Run `nmap --version` to check your Nmap version.  
- Use `sudo` (or admin) for scans requiring raw sockets (`-sS`, `-O`, `-sI`, etc.).  
- Always have **explicit permission** before scanning any network or host.

---

## 🧭 Host Discovery
```bash
# Ping scan (discover live hosts, no ports)
nmap -sn 192.168.1.0/24

# ARP scan (fast & accurate on local LAN)
nmap -PR 192.168.1.0/24

# ICMP Echo / Timestamp / Netmask probes
nmap -sn -PE -PP -PM 10.0.0.0/24

# Treat hosts as online (skip discovery)
nmap -Pn 203.0.113.5
```

---

## 🔓 Port Scans — Common Types
```bash
# TCP Connect (no privileges required)
nmap -sT target

# SYN (stealth) scan — fast, requires privileges
sudo nmap -sS target

# UDP scan (slow)
sudo nmap -sU -p 53,67,68,123 target

# ACK scan (firewall mapping)
nmap -sA target

# FIN / Xmas / Null (evade naive filters)
sudo nmap -sF target
sudo nmap -sX target
sudo nmap -sN target
```

---

## 🧬 Service & Version Detection
```bash
# Detect service and version
nmap -sV target

# Combine with SYN scan & specific ports
sudo nmap -sS -sV -p22,80,443 target
```

---

## 🧪 OS Detection
```bash
# OS detection (requires privileges)
sudo nmap -O target

# Aggressive scan (OS + version + scripts + traceroute)
sudo nmap -A target
```

---

## 🧠 NSE (Nmap Scripting Engine)
```bash
# Default scripts
nmap -sC target

# Run a category (vuln, brute, discovery, etc.)
nmap --script=vuln target

# Run specific scripts
nmap --script=http-enum,ssl-heartbleed target

# Pass script arguments
nmap --script http-brute --script-args userdb=users.txt,passdb=passes.txt target

# Debug script execution
nmap --script-trace --script http-enum target

# Get help for a script
nmap --script-help http-enum
```

---

## 📁 Output Formats
```bash
# Normal (human readable)
nmap -oN results.nmap target

# XML (parser-friendly)
nmap -oX results.xml target

# Grepable
nmap -oG results.gnmap target

# Save all formats (basename.nmap, .xml, .gnmap)
nmap -oA scan-results target

# Resume interrupted all-format scan (use basename.nmap)
nmap --resume scan-results.nmap
```

---

## ⏱ Timing & Port Selection
```bash
# Scan all TCP ports 1-65535
sudo nmap -p- target

# Scan top N most common ports
nmap --top-ports 100 target

# Timing templates (0 slow — 5 fastest)
nmap -T3 target    # safe
nmap -T4 target    # faster (aggressive)
```

Tuning examples:
```bash
# Set minimum packet rate
nmap --min-rate 100 target

# Decrease retries for speed
nmap --max-retries 2 target

# Set host-level timeout
nmap --host-timeout 30m target
```

---

## 🛡 Evasion & Advanced Techniques (Use Cautiously)
```bash
# Fragment packets
sudo nmap -f target

# Use decoys (adds source confusion)
sudo nmap -D decoy1,decoy2,ME target

# Spoof source port (requires privileges)
sudo nmap -g 53 target

# Idle/Zombie scan (requires a suitable zombie)
sudo nmap -sI zombie_host target

# Adjust data payload length
sudo nmap --data-length 50 target

# Set MTU
sudo nmap --mtu 24 target
```

---

## 🔍 Debugging & Analysis Helpers
```bash
# Show only open (or possibly open) ports
nmap --open target

# Show why Nmap thinks a port is in a state
nmap --reason target

# Show packet-level trace (lots of output)
sudo nmap --packet-trace target

# Run traceroute with the scan
nmap --traceroute target

# List network interfaces and routing
nmap --iflist
```

---

## 📚 Example Workflows (Copy & Run)
```bash
# Quick reconnaissance: discover hosts and scan top ports
nmap -sn 10.0.0.0/24
nmap --top-ports 100 -T4 10.0.0.5

# Full host scan (OS, services, scripts), save outputs
sudo nmap -A -sV -O -p- -T4 -oA lab-scan-10-0-0-5 10.0.0.5

# Targeted web vuln scan
nmap -sS -sV --script=vuln -p 80,443 target
```

---

## ✅ Practical Notes for Labs
- Prefer `-T3` in noisy/lab environments to reduce false positives.  
- Use `--open` when you only care about open ports in grepable output.  
- Keep `-oA` results in a `results/` folder for easy sharing and parsing.  
- Document the Nmap command and the Nmap version in lab notes.

---

## ⚖ Legal & Ethical
Only scan systems you **own** or have **explicit permission** to test. Unauthorized scanning can be illegal and harmful.

---

