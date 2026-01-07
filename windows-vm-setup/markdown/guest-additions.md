# 📦 VirtualBox Guest Additions Installation

This document explains how to install VirtualBox Guest Additions on the Windows 10 SOC VM. Guest Additions improve usability by enabling clipboard sharing, drag‑and‑drop, display scaling, and seamless mouse integration.

---

## 📥 Prerequisites
- Windows 10 VM already installed and running
- VirtualBox installed on host system
- ISO for Guest Additions included with VirtualBox

---

## ⚙️ Installation Steps
1. Start the Windows 10 VM
2. In the VM window, go to **Devices → Insert Guest Additions CD Image**
3. Open **File Explorer** inside the VM → Navigate to the mounted CD drive
4. Run `VBoxWindowsAdditions.exe` as Administrator
5. Follow the installer prompts:
   - Accept license agreement
   - Install all components
   - Allow driver installation if prompted
6. Reboot the VM after installation completes

✅ *Verification*: After reboot, check that clipboard sharing and display resizing work.  
📸 *Screenshot*: `images/guest-additions.png`

---

## 🔎 Features Enabled
- **Clipboard integration**: Copy/paste between host and VM
- **Drag‑and‑drop**: Move files between host and VM
- **Display scaling**: Auto‑resize VM window
- **Mouse pointer integration**: Seamless movement without capture/release

✅ *Verification*: Resize VM window and confirm resolution adjusts automatically.  
📸 *Screenshot*: `images/display-scaling.png`

---

## 🛠️ Troubleshooting
- If installer fails:
  - Ensure VM is running Windows 10 (64‑bit)
  - Check that ISO is mounted correctly
  - Run installer as Administrator
- If features don’t work:
  - Reboot VM
  - Reinstall Guest Additions
  - Verify VirtualBox version is up to date

---

## 🔗 Next Steps
- Proceed to [`soc-prep.md`](soc-prep.md) for SOC hardening and tool installation
- Confirm networking setup in [`windows-install.md`](windows-install.md)

---

## 🎯 Goal
Enable smooth usability and integration features for the Windows 10 SOC VM.
