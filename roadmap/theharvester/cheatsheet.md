# ⚡ theHarvester Cheatsheet

Quick reference for flags, syntax, and common usage.

---

## 🧪 Basic Syntax

```bash
theharvester -d <domain> -b <source> [options]
```

## 🔑 Common Flags

| Flag | Description |
|------|-------------|
| `-d` | Target domain (e.g., `example.com`) |
| `-b` | Data source (e.g., `google`, `bing`, `linkedin`, `shodan`) |
| `-l` | Limit number of results (default: `100`) |
| `-f` | Save output to file (HTML or XML) |
| `-s` | Start with result number `X` (useful for pagination) |
| `-v` | Verbose output (more details during execution) |
| `-h` | Help menu (show available options) |

---

## 🌐 Popular Data Sources

- google
- bing
- linkedin
- shodan
- crtsh
- all → Use all available sources


## 🧠 Sample Commands

- Basic scan using Google:
```
theharvester -d tesla.com -b google
```
- Scan with all sources and save output:
```
theharvester -d cyber.gov.in -b all -l 200 -f output/cyber_recon.html
```
---

## 🛠 Troubleshooting Tips

| Symptom          | Fix                                                   |
|------------------|--------------------------------------------------------|
| No results       | Try a different source or reduce `-l`                 |
| HTML not saving  | Use full path with `-f`                               |
| Tool not found   | Run `which theharvester` or reinstall                 |
| Python error     | Run `pip3 install -r requirements.txt`                |

## 🧭 Workflow Tip

- Use harvested subdomains and IPs with:
- Nmap → for port scanning
- dnsenum → for DNS enumeration
- Gobuster → for directory brute-forcing

## ⚖️ Reminder

Only scan domains you’re authorized to test. Stay ethical.

