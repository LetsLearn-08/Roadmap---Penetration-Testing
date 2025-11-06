# 🕵️ theHarvester – OSINT Reconnaissance Tool

## 📌 What Is theHarvester?

**theHarvester** is a powerful tool used in the **reconnaissance phase** of ethical hacking. It helps gather publicly available information (OSINT) about a target domain — without touching the target’s systems. This includes:

- 📧 Email addresses
- 🌐 Subdomains
- 🖥 IP addresses
- 🏷 Hostnames

This data helps map out the target’s digital footprint before deeper scanning or exploitation.

---

## 🎯 Objective

Use theHarvester to perform OSINT on a target domain and extract actionable data (emails, subdomains, IPs) for further scanning.

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

## 🔑 Common Flags

| Flag | Description |
|------|-------------|
| `-d` | Target domain (e.g., `example.com`) |
| `-b` | Data source (e.g., `google`, `bing`, `linkedin`, `shodan`) |
| `-l` | Limit number of results |
| `-f` | Save output to HTML or XML |
| `-h` | Help menu |

## 🧠 Sample Commands

Scan using Google:
```
theharvester -d tesla.com -b google
```
Use all sources and save output:
```
theharvester -d cyber.gov.in -b all -l 200 -f output/cyber_recon.html
```

## 📊 Output Breakdown

- Emails: Useful for phishing simulations or awareness training
- Subdomains: Reveal hidden services like admin.example.com
- IP addresses: Can be scanned later with tools like Nmap
- Hostnames: Show internal naming patterns (e.g., mail01, dev-server)

## 🧭 Workflow Integration

- Run theHarvester to gather OSINT
- Feed subdomains/IPs into Nmap or Masscan
- Use Gobuster or Nikto for deeper enumeration
- Document findings in your lab journal or markdown tracker

## 🛠️ Troubleshooting

| Issue                         | Cause                                      | Solution                                                         |
|------------------------------:|-------------------------------------------:|------------------------------------------------------------------|
| `ModuleNotFoundError`         | Missing Python dependencies                | Run `pip3 install -r requirements.txt`                           |
| No results from search engine  | API limits or outdated source              | Try a different source (e.g. `-b bing`, `-b all`) or reduce `-l` |
| HTML report not saving         | Incorrect file path or permissions         | Use full path: `-f /home/user/reports/output.html`               |
| Tool not found                 | Not installed or wrong environment         | Verify with `which theharvester` or reinstall manually           |

## 🧪 Debug Tips

- Run with -h to confirm syntax
- Use -l 10 for quick test runs
- Check internet connectivity if sources return empty
-  Use verbose mode (if available) for deeper logs

## 📋 Status Tracking

| Task                   | Status | Notes                                           |
|------------------------|:------:|-------------------------------------------------|
| Tool installed         | ✅     | Verified on Kali Linux                          |
| Basic scan tested      | ✅     | Used `tesla.com` with `google`                  |
| Multi-source scan      | ✅     | Used `cyber.gov.in` with `-b all`               |
| HTML report saved      | ✅     | Saved to `output/cyber_recon.html`              |
| Output interpretation  | 🔄     | Add annotated findings                          |
| Integration with Nmap  | ⏳     | Will feed IPs/subdomains into next phase        |

## ⚖️ Ethical Reminder
OSINT tools like theHarvester are legal and powerful — but only when used ethically. Never scan or collect data from domains you don’t own or have permission to test. Always stay within your scope.

## 🧠 Slogan
Learn to see what others miss — one domain at a time. Recon isn’t noisy. It’s quiet, smart, and strategic. theHarvester helps you listen to the internet’s whispers.







