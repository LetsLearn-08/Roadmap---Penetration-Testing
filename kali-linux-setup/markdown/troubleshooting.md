# 🛠️ Troubleshooting Guide: Kali Linux Setup Lab

This guide documents common issues encountered during the setup of Kali Linux and Metasploitable2 in VirtualBox, along with practical fixes and verification steps.

---

## 🐧 Kali Linux VM Issues

### 🔸 Problem: Black screen or stuck boot
**Fixes:**
- Check if ISO is corrupted — re-download from [kali.org](https://www.kali.org/get-kali/)
- Increase RAM to at least 2048 MB
- Enable EFI in VM settings if needed

### 🔸 Problem: No internet access in Kali
**Fixes:**
- Ensure Adapter 1 is set to NAT
- Run: `ping google.com` to verify DNS
- Try: `sudo dhclient` to renew IP

---

## 💣 Metasploitable2 VM Issues

### 🔸 Problem: Disk not detected
**Fixes:**
- Use “Add existing disk” in Storage → Controller → Choose `.vmdk`
- Make sure the disk is attached to IDE controller, not SATA

### 🔸 Problem: Boot errors or kernel panic
**Fixes:**
- Re-extract `.zip` file properly
- Avoid renaming `.vmdk` file manually

---

## 🌐 Networking Issues

### 🔸 Problem: Kali can't ping Metasploitable
**Fixes:**
- Confirm both VMs use the same Host-Only Adapter (e.g., `vboxnet0`)
- Check IPs:
  - Kali: `ip a`
  - Metasploitable: `ifconfig`
- Restart VirtualBox networking service

### 🔸 Problem: Host-only adapter missing
**Fixes:**
- Go to VirtualBox → File → Host Network Manager → Create new adapter
- Set IP: `192.168.56.1`, Subnet: `255.255.255.0`

---

## 🧪 Verification Checklist

- ✅ Kali boots and logs in successfully
- ✅ Metasploitable boots to login prompt (`msfadmin`)
- ✅ Both VMs have IPs in `192.168.56.x` range
- ✅ Ping works between Kali and Metasploitable

---

## 📝 Notes

- Always document IP addresses and adapter names
- Use `netstat`, `ip a`, and `ifconfig` for quick diagnostics
- Keep your markdown sheets updated as you troubleshoot

