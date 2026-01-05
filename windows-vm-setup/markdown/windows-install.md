# 🖥️ Windows 10 VM Installation Guide

This document explains how to install and configure a Windows 10 virtual machine in Oracle VirtualBox for SOC lab use. Follow these steps to replicate a stable endpoint environment.

---

## 📥 Prerequisites
- **Windows 10 ISO**: Download from Microsoft’s official site
- **Oracle VirtualBox**: Latest version installed
- **Host system resources**: At least 8 GB RAM, 2 CPU cores, 60 GB free disk

---

## ⚙️ VM Creation
1. Open VirtualBox → **New VM**
2. Name: `Win10-SOC`
3. Type: `Microsoft Windows`
4. Version: `Windows 10 (64-bit)`
5. Allocate:
   - RAM: **6144 MB**
   - CPU: **2 cores**
   - Disk: **50 GB (VDI, dynamically allocated)**
6. Mount ISO:
   - Settings → Storage → SATA Port 1 → Attach `Windows.iso`
7. Boot order:
   - **Optical → Hard Disk**


---

## 💿 Installation
1. Start VM → Boot from ISO
2. Select language, keyboard, and region
3. Choose **Custom Install**
4. Create new partition on 50 GB disk
5. Proceed with installation (auto reboots)
6. Configure initial user account and password

✅ *Verification*: Windows desktop loads successfully.  

---

## 🛠️ Post‑Install Setup
1. Install **VirtualBox Guest Additions**:
   - Devices → Insert Guest Additions CD
   - Run installer → Enable clipboard, drag‑and‑drop, display scaling
2. Update Windows via Settings → Update & Security
3. Create snapshot:
   - Name: `Win10_BaseInstall_ReadyForTools`

✅ *Verification*: Guest Additions features working (resize, clipboard).  


---

## 🔎 Next Steps
- Proceed to [`soc-prep.md`](soc-prep.md) for SOC hardening and tool installation
- Verify networking setup in [`guest-additions.md`](guest-additions.md)
- Track progress in [`status.md`](status.md)

---

## 🎯 Goal
Provide a reproducible Windows 10 VM baseline for SOC detection workflows.
