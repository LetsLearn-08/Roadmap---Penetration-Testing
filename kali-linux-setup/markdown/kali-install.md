# Kali Linux VM Installation Guide

## 🔧 Requirements
- Oracle VirtualBox (version X.X.X)
- Kali Linux ISO (download from [kali.org](https://www.kali.org/get-kali/))

## 🖥️ Steps
1. **Create a new VM** in VirtualBox:
   - Name: `Kali-Linux`
   - Type: Linux
   - Version: Debian (64-bit)

2. **Allocate resources**:
   - RAM: 2048 MB or higher
   - CPU: 2 cores (recommended)

3. **Attach Kali ISO**:
   - Storage → Add optical drive → Choose Kali ISO

4. **Start VM and install Kali**:
   - Choose graphical install
   - Set hostname, username, password
   - Use guided disk partitioning
   - Install GRUB bootloader

5. **Post-install setup**:
   - Update system: `sudo apt update && sudo apt upgrade`
   - Install tools: `sudo apt install net-tools curl git`

## ✅ Status
VM installed and booting successfully.
