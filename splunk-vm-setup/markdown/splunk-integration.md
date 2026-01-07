# 🔗 Splunk Integration with Windows SOC VM

This document explains how to forward Windows logs into Splunk for centralized analysis.

---

## 📥 Prerequisites
- Splunk VM running (`splunk-install.md`)
- Windows SOC VM with Sysmon + Winlogbeat/NXLog installed

---

## ⚙️ Splunk Configuration
1. Edit `inputs.conf`:

   ```conf
   [tcp://5044]
   connection_host = ip
3. Restart Splunk:
   ```bash
   sudo /opt/splunk/bin/splunk restart
✅ *Verification*: Splunk listening on port 5044.
📸 *Screenshot*: `images/splunk-inputs.png`.
