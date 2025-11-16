# 📚 Unit 1: Installation & Interface Basics

## 🎯 Objective
Learn how to install Wireshark on different operating systems and understand the basics of its interface.

---

## 🛠 Installation

### Linux (Kali / Ubuntu)
```bash
sudo apt update
sudo apt install wireshark
sudo usermod -aG wireshark $USER
```
Log out and back in for group changes to take effect.

Verify installation:
 ```
  wireshark --version
 ```
### Windows

- Download installer from wireshark.org.
- Run setup wizard and install Npcap when prompted.
- Launch Wireshark from Start Menu.

## 💻 Windows Installation

Download Wireshark for Windows from the official site:

- [Windows x64 Installer](https://www.wireshark.org/download/win64) → Standard installer for most systems  
- [Windows Arm64 Installer](https://www.wireshark.org/download/winarm64) → For ARM‑based devices  
- [Windows PortableApps®](https://www.wireshark.org/download/portableapps) → Portable version, no installation required  

⚠️ During installation, ensure **Npcap** is selected — it’s required for packet capture.


### macOS

- Download .dmg from wireshark.org.
- Drag Wireshark into Applications folder.
- Launch Wireshark from Applications.

## 🍎 macOS Installation

Download Wireshark for macOS from the official site:

- [macOS Universal Disk Image](https://www.wireshark.org/download.html) → Works on Intel & Apple Silicon  
- [macOS Arm Disk Image](https://www.wireshark.org/download.html) → Optimized for Apple Silicon (M1/M2)  
- [macOS Intel Disk Image](https://www.wireshark.org/download.html) → Optimized for Intel Macs  

⚠️ After installation, grant Wireshark **packet capture permissions** in macOS Security & Privacy settings.


## ▶️ Launching Wireshark

- Open Wireshark.
- Select an interface (Ethernet, Wi‑Fi, or Loopback).
- Click the blue shark fin 🦈 to start capturing.
- Stop capture with the red square button when done.

## 🔍 Interface Basics

- Packet List Pane → Displays all captured packets in sequence.
- Packet Details Pane → Shows protocol layers (Ethernet, IP, TCP, etc.).
- Packet Bytes Pane → Raw data in hex and ASCII.
- Filter Toolbar → Apply display filters (e.g., http, icmp).
- Color Coding → Helps distinguish protocols quickly.

## 📸 Documentation

- Screenshot: Wireshark main interface with capture running.
- Screenshot: Example of packet details pane expanded.
- Notes: Interface navigation and filter usage.

## ✅ Outcome

By completing this unit, you will:

- ✅ Install Wireshark on your system.
- ✅ Launch and start capturing packets.
- ✅ Understand the three main panes of the interface.
- ✅ Apply basic display filters to focus on specific traffic.
