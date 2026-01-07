# 📦 Splunk Enterprise Installation Guide

This document explains how to install Splunk Enterprise on an Ubuntu Server VM inside VirtualBox.

---

## 📥 Prerequisites
- Ubuntu Server ISO (latest LTS recommended)
- VirtualBox installed on host
- At least 4 GB RAM, 2 CPU cores, 40 GB disk

---

## ⚙️ VM Creation
1. Create new VM → Name: `Splunk-SIEM`
2. Type: `Linux`, Version: `Ubuntu (64-bit)`
3. Allocate resources:
   - RAM: **4096 MB**
   - CPU: **2 cores**
   - Disk: **40 GB**
4. Networking:
   - Adapter 1: NAT
   - Adapter 2: Host‑only (`192.168.56.0/24`)

✅ *Verification*: Check VM settings screen.  
📸 *Screenshot*: `images/splunk-vm-settings.png`

---

## 💿 OS Installation
1. Boot VM with Ubuntu ISO
2. Install Ubuntu Server (minimal install recommended)
3. Create user `splunkadmin`

✅ *Verification*: Login prompt appears.  
📸 *Screenshot*: `images/ubuntu-login.png`

---

## 🛠️ Splunk Installation
1. Download Splunk Enterprise `.deb` package from official site
2. Install via:
   ```bash
   sudo dpkg -i splunk*.deb
3. Enable Splunk as a service:
   ```bash
   sudo /opt/splunk/bin/splunk enable boot-start
4. Start Splunk:
   ```bash
   sudo /opt/splunk/bin/splunk start
5. Access web UI: http://<vm-ip>:8000

✅ *Verification*: Splunk login page loads.
📸 *Screenshot*: `images/splunk-web-login.png`
