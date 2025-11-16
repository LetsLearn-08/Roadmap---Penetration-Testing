# 📘 Cheatsheet: Wireshark Shortcuts & Workflow Tips

## 🎯 Objective
Boost productivity in Wireshark with essential **keyboard shortcuts** and workflow tricks.

---

## ⌨️ Keyboard Shortcuts

- **Ctrl + E** → Start/Stop capture  
- **Ctrl + K** → Restart current capture  
- **Ctrl + Shift + P** → Preferences  
- **Ctrl + F** → Find packet  
- **Ctrl + G** → Go to packet number  
- **Ctrl + M** → Mark/unmark packet  
- **Ctrl + N** → New Wireshark window  
- **Ctrl + R** → Reload capture file  
- **Ctrl + H** → Toggle packet details pane  
- **Ctrl + I** → Toggle packet list pane  
- **Ctrl + T** → Toggle packet bytes pane  
- **Ctrl + L** → Show packet length column  

---

## 🛠 Workflow Tips

- Use **display filters** (`http`, `icmp`, `arp`) to narrow down analysis quickly.  
- Right‑click a packet → **Follow TCP Stream** to view full conversations.  
- Save frequent filters in the **filter toolbar** for one‑click access.  
- Use **coloring rules** to highlight suspicious traffic (e.g., SYN packets).  
- Export packets (`File → Export Specified Packets`) for sharing or deeper analysis.  
- Combine filters with logical operators:  
  - `ip.src == 192.168.1.5 and tcp.port == 80`  

---

## ✅ Outcome
By using these shortcuts and tips, you can:  
- ✅ Navigate Wireshark faster  
- ✅ Focus on relevant traffic with minimal clicks  
- ✅ Improve efficiency during labs and real‑world analysis
