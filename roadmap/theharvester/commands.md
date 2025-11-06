# 🧭 theHarvester – Command Walkthrough

This file provides a quick, actionable walkthrough for using theHarvester in your recon lab.

---

## ✅ Step 1: Select Target Domain

Choose a public domain for OSINT scanning:

```bash
tesla.com
cyber.gov.in
```
## ✅ Step 2: Run Basic Scan

Use a single data source like Google:

```
theharvester -d tesla.com -b google
```
## ✅ Step 3: Run Multi-Source Scan

Use all available sources and save output:
```
theharvester -d cyber.gov.in -b all -l 200 -f output/cyber_recon.html
```

## ✅ Step 4: Review Output

Look for:

- 📧 Email addresses
- 🌐 Subdomains
- 🖥 IP addresses
- 🏷 Hostnames

## ✅ Step 5: Document Findings

- Save screenshots in screenshots/
- Annotate results in markdown
- Link findings to next-phase tools like Nmap

## 🧠 Tips

- Use -l 10 for quick test runs
- Always check syntax with theharvester -h
- Respect ethical boundaries — only scan domains you’re authorized to test

