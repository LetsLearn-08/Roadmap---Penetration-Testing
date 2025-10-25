# 🧠 Nmap Weekly Journal – Overview & Key Learnings

## 📌 What is Nmap?
Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. It helps identify live hosts, open ports, running services, and operating systems on a network. This week, I explored core scan types using Kali Linux against Metasploitable2 in a host-only lab setup.

---

## 🛠️ Lab Environment
- **Attacker VM**: Kali Linux (VirtualBox)
- **Target VM**: Metasploitable2
- **Network Mode**: Host-only Adapter
- **Tool Version**: Nmap 7.94
- **IP Check**: `ip a` (Kali), `ifconfig` (Metasploitable)

---

## 🔍 Scan Types & Examples

1. Ping Scan (Host Discovery)
```bash
nmap -sn <target>
``` 
- Checks which hosts are up without scanning ports.
  
 #### 📝 Notes:
 - Fast and non-intrusive.
 - Useful for host discovery before deeper scans.

2.TCP Connect Scan
```bash
nmap -sT <target>
```
- Uses full TCP connection — easy to detect, but reliable.

#### 📝 Notes:
- Default and widely used.
- Requires root privileges.

Less likely to be logged by the target.

3.SYN Scan (Stealth Scan)
```bash
nmap -sS <target>
```
- Sends SYN packets — fast and stealthy.
  
#### 📝 Notes:
- Default and widely used.
- Requires root privileges.

Less likely to be logged by the target.



5.Service & Version Detection
```bash
nmap -sV <target>
```
- Identifies running services and their versions.
  
#### 📝 Notes:
- Helps identify vulnerable software versions.
- Combine with -sS for better results.


6.OS Detection
```
nmap -O <target>
```
- Guesses the OS based on TCP/IP stack behavior.

#### 📝 Notes:
- Accuracy improves with more open ports.
- May not always be 100% reliable.

7.Aggressive Scan
```
nmap -A <target>
```
Combines OS detection, version detection, script scanning, and traceroute.

#### 📝 Notes:
- Very detailed output.
- Noisy and easily detectable.
- Great for quick recon in labs.

8.NSE Script Scan
```
nmap --script vuln <target>
```
Runs vulnerability detection scripts from the Nmap Scripting Engine.

#### 📝 Notes:

- Use --script-help <script> to understand what each script does.
- Powerful for targeted enumeration.

## 🧾 Output Options

- -oN: Normal output
- -oX: XML output
- -oG: Grepable output
- -oA: All formats

Example:
```
nmap -sV -oA scan_results <target>
```

## 🧠 Advanced Scan Types


### 9. UDP Scan — `-sU`
```bash
sudo nmap -sU <target-ip>
```
Scans for open UDP ports. UDP scanning is **slower** and **less reliable** than TCP scanning.

**📝 Notes**
- Useful for discovering UDP-based services such as DNS (53), SNMP (161), NTP (123), and various custom services.
- UDP responses may be silent (no reply) — Nmap infers open|filtered when it gets no response, so **false positives** (or ambiguous results) are common.
- Often requires root privileges for raw socket access (hence `sudo`).
- Scans can be slow because many UDP services implement rate-limiting or do not respond at all.

**⚠️ Lab tip**
- Use in controlled/lab environments. Combine with service-specific tools (e.g., `dig`, `snmpwalk`) to confirm results.

---

### 10. TCP Connect Scan — `-sT`
```bash
nmap -sT <target-ip>
```
Performs a **full TCP handshake** to detect open ports (connect() syscall).

**📝 Notes**
- Easier to detect and more likely to be logged on the target because it completes full connections.
- Does **not** require root privileges (useful when you don't have raw-socket access).
- Slightly slower and noisier than SYN scan (`-sS`) because it completes the handshake.

**⚠️ Lab tip**
- Good when you cannot run Nmap as root or when you want a simple, reliable open/closed determination.

---

### 11. Firewall Evasion — fragmentation with `-f`
```bash
nmap -sS -f <target-ip>
```
Uses packet fragmentation to split probe packets into smaller fragments which may bypass basic packet filters.

**📝 Notes**
- May help evade simplistic or misconfigured firewall/IDS rules that don't properly reassemble fragments.
- `-f` fragments packets; combining with SYN scan (`-sS`) is common.
- Modern IDS/IPS and firewalls frequently reassemble fragments, so fragmentation **is not guaranteed** to bypass detection.

**⚠️ Legal & ethical**
- Use **only** in labs or on targets explicitly authorized for testing. Evading defenses on real targets without permission is illegal.

---

### 12. Timing & Performance Tuning — `-T<0..5>`
```bash
nmap -T4 <target-ip>
```
Controls scan timing and performance. Values range from `-T0` (paranoid) to `-T5` (insane).

**📝 Notes**
- `-T0` — paranoid (very slow, used for stealth).
- `-T1` — sneaky.
- `-T2` — polite.
- `-T3` — normal (default).
- `-T4` — aggressive (good balance for labs; faster, more concurrent probes).
- `-T5` — insane (very fast; likely to be detected and may create lots of noise or false results).
- Higher timing templates increase speed but also increase likelihood of detection, missed responses, and false positives/negatives on unstable networks.

**⚠️ Lab tip**
- Use `-T4` for internal lab scans where speed matters. Use `-T2`/`-T3` or custom timing when scanning production or sensitive environments.

---

### Example combined command (lab)
```bash
sudo nmap -sU -sS -T4 -p 1-2000 <target-ip>
```
- Scans UDP and SYN (TCP) ports 1–2000 with aggressive timing.
- Use in controlled labs only.

---

 ## ✅ Key Takeaways

- **Always verify IPs before scanning.**  
  Ensure you have the correct target and explicit authorization.

- **Use `-v` or `-vv` for verbose output during troubleshooting.**  
  Verbose modes help reveal timing, retries, and probe behavior.

- **Document each scan with:**
  - **Command used** (copy the exact command).
  - **Screenshot** (terminal or results viewer).
  - **Observations** (open/closed/filtered, anomalies, timestamps).

- **Organize scans by type** (e.g., `UDP`, `SYN`, `Connect`, `Evasion`) for easy review and comparison.

- **NSE scripts and timing flags offer deeper control.**  
  Learn `--script` categories and combine with timing templates carefully.

---

## 🚀 Next Steps

- **Explore `--script http-*`** for web service enumeration (e.g., discovery, vulnerability checks, content enumeration).
- **Compare scan results with and without firewalls** to understand how filtering/IDS changes output.
- **Add markdown tables** to compare scan outputs (open ports, service versions, timestamps, notes).
- **Try saving results** with Nmap output options:
  - `-oN <file>` — normal format
  - `-oX <file>` — XML
  - `-oG <file>` — grepable (good for quick parsing)
- **Optional:** Automate a small recorder script that runs scans, saves outputs (`-oX`), and appends a short observation note to a CSV/MD log.

---

### Markdown table template 
| Scan Type | Command | Ports Scanned | Results File | Observations |
|---|---|---:|---|---|



