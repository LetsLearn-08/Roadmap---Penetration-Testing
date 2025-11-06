# 🕵️ theHarvester – OSINT Reconnaissance Tool

## 📌 What Is theHarvester?

**theHarvester** is a powerful tool used in the **reconnaissance phase** of ethical hacking. It helps gather publicly available information (OSINT) about a target domain — without touching the target’s systems. This includes:

- 📧 Email addresses
- 🌐 Subdomains
- 🖥 IP addresses
- 🏷 Hostnames

This data helps map out the target’s digital footprint before deeper scanning or exploitation.

---
# 🕵️ theHarvester – OSINT Reconnaissance Tool

## 🎯 Objective
Use theHarvester to perform OSINT on a target domain and extract actionable data (emails, subdomains, IPs) for further scanning.

## 📁 Contents
- [`harvester.md`](harvester.md): Full tool guide and usage
- [`commands.md`](commands.md): Quick walkthrough
- [`cheatsheet.md`](cheatsheet.md): Flag reference (optional)
- [`screenshots/`](screenshots/): Scan visuals
- [`output/`](output/): Saved results

## 🔗 Next Steps
Use findings with:
- [Nmap Lab](../nmap/nmap.md)
- [dnsenum Lab](../dnsenum/dnsenum.md)

---

## ⚙️ Installation

### ✅ Kali Linux
Pre-installed. Just run:
```bash
theharvester -h
```
## 🛠 Manual Installation
```
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
sudo pip3 install -r requirements.txt
```
## 🧪 Basic Syntax
```
theharvester -d <target-domain> -b <data-source>
```
---

## 🔑 Common Flags

| Flag | Description |
|------|-------------|
| `-d` | Target domain (e.g., `example.com`) |
| `-b` | Data source (e.g., `google`, `bing`, `linkedin`, `shodan`) |
| `-l` | Limit number of results |
| `-f` | Save output to HTML or XML |
| `-h` | Help menu |

---

## 🧠 Sample Commands

- Scan using Google:
```
theharvester -d tesla.com -b google
```
- Use all sources and save output:
```
theharvester -d cyber.gov.in -b all -l 200 -f cyber_recon.html
```
## 📊 Output Breakdown

- Emails: Useful for phishing simulations or awareness training
- Subdomains: Reveal hidden services like admin.example.com
- IP addresses: Can be scanned later with tools like Nmap
- Hostnames: Show internal naming patterns (e.g., mail01, dev-server)

## 🧭 Workflow Integration

- Run theHarvester to gather OSINT.
- Feed subdomains/IPs into Nmap or Masscan.
- Use Gobuster or Nikto for deeper enumeration.
- Document findings in your lab journal or markdown tracker.

---
---

## 🛠️ Troubleshooting

### ❌ Common Issues & Fixes

| Issue | Cause | Solution |
|------|-------|----------|
| `ModuleNotFoundError` | Missing Python dependencies | Run `pip3 install -r requirements.txt` |
| No results from search engine | API limits or outdated source | Try a different source (`-b bing`, `-b all`) or reduce `-l` |
| HTML report not saving | Incorrect file path or permissions | Use full path: `-f /home/user/reports/output.html` |
| Tool not found | Not installed or wrong environment | Verify with `which theharvester` or reinstall manually |

### 🧪 Debug Tips
- Run with `-h` to confirm syntax.
- Use `-l 10` for quick test runs.
- Check internet connectivity if sources return empty.
- Use verbose mode (if available) for deeper logs.

---

## 📋 Status Tracking

| Task | Status | Notes |
|------|--------|-------|
| Tool installed | ✅ | Verified on Kali Linux |
| Basic scan tested | ✅ | Used `tesla.com` with `google` |
| Multi-source scan | 🔄 | Planned with `cyber.gov.in` and `-b all` |
| HTML report saved | 🔄 | To be tested with `-f` flag |
| Output interpretation | 🔄 | Pending analysis and markdown notes |
| Integration with Nmap | ⏳ | Will feed IPs/subdomains into next phase |

---

## 🧪 Lab Module: Recon with theHarvester

### 🎯 Objective

Use theHarvester to perform OSINT on a target domain and extract actionable data for further scanning.

### 🧭 Steps

1. **Select Target**  
   Choose a public domain (e.g., `tesla.com`, `cyber.gov.in`)

2. **Run Basic Scan**
   ```
   theharvester -d tesla.com -b google
   ```
3. **Run Multi-Source Scan**
```
theharvester -d cyber.gov.in -b all -l 200 -f cyber_recon.html
```
4. **Review Output**

  - Emails
  - Subdomains
  - IPs
  - Hostnames

5. **Document Findings**

  - Save screenshots
  - Annotate results
  - Link findings to next phase tools (e.g., Nmap)

## 🧠 Tips for Beginners

  - Use -b all to maximize coverage.
  - Try scanning public domains like tesla.com, microsoft.com, or cyber.gov.in.
  - Always check the help menu: theharvester -h
  - Respect ethical boundaries — only scan domains you’re authorized to test.

## ⚖️ Ethical Reminder

  OSINT tools like theHarvester are legal and powerful — but only when used ethically. Never scan or collect data from domains you don’t own or have permission to test. Always stay within your scope.

## 🔗 Related Tools

- Nmap(https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/blob/main/roadmap/nmap/overview.md) – Scan IPs and ports found by theHarvester
- Netcat(https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/blob/main/roadmap/netcat/overview.md) – Test open ports and banner grabbing



---

Let me know when you want help building the cheat sheet, linking this to your weekly journal, or starting the Nmap follow-up scan. We can turn this into a full recon pipeline.

# Learn to see what others miss — one domain at a time...






