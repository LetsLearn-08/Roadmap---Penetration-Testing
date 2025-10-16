# 🧾 Nmap Scan Cheatsheet

A quick reference guide for common Nmap scan types, flags, and usage examples.

---

## 🔍 Host Discovery

| Command | Description |
|--------|-------------|
| `nmap -sn <target>` | Ping scan to check if host is up |
| `nmap -Pn <target>` | Skip ping (useful if ICMP is blocked) |

---

## 🔓 Port Scanning

| Command | Description |
|--------|-------------|
| `nmap -p- <target>` | Scan all 65535 TCP ports |
| `nmap -F <target>` | Fast scan (100 most common ports) |
| `nmap -p 21,22,80 <target>` | Scan specific ports |

---

## 🔧 Scan Techniques

| Command | Description |
|--------|-------------|
| `nmap -sS <target>` | SYN scan (stealthy, default) |
| `nmap -sT <target>` | TCP connect scan |
| `nmap -sU <target>` | UDP scan |
| `nmap -sN <target>` | Null scan (no flags set) |

---

## 🧠 Service & OS Detection

| Command | Description |
|--------|-------------|
| `nmap -sV <target>` | Detect service versions |
| `nmap -O <target>` | Detect operating system |
| `nmap -A <target>` | Aggressive scan (OS + version + script + traceroute) |

---

## 🧪 NSE Script Scanning

| Command | Description |
|--------|-------------|
| `nmap --script vuln <target>` | Run vulnerability scripts |
| `nmap --script default <target>` | Run default scripts |
| `nmap --script-help <script>` | Show script description |

---

## 📝 Output Options

| Command | Description |
|--------|-------------|
| `-oN <file>` | Normal output |
| `-oG <file>` | Grepable output |
| `-oX <file>` | XML output |
| `-oA <prefix>` | All formats (adds .nmap, .gnmap, .xml) |

---

## 🧱 Firewall Evasion

| Command | Description |
|--------|-------------|
| `nmap -f <target>` | Fragment packets |
| `nmap --data-length 50 <target>` | Obfuscate packet size |
| `nmap -D RND:10 <target>` | Decoy scan |
| `nmap -T0` to `-T5` | Timing (0 = slowest, 5 = fastest) |

---

## 🧠 Tips

- Use `-v` or `-vv` for verbose output
- Combine flags: `nmap -sS -sV -O -p- <target>`
- Always scan in a legal, controlled environment

---

Happy scanning! 🛡️
