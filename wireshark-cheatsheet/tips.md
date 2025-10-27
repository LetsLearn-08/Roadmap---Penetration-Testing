# 🧠 Wireshark Pro Tips

These tips will help you analyze packets faster, spot anomalies, and get more out of Wireshark during labs and real-world troubleshooting.

---

## 🎨 Use Coloring Rules

- Go to `View → Coloring Rules`
- Highlight suspicious traffic (e.g., TCP RST, ICMP errors)
- Helps visually separate protocols and anomalies

---

## 🔍 Follow Streams

- Right-click a packet → “Follow → TCP Stream”
- Reconstruct conversations (e.g., login attempts, file transfers)
- Works for HTTP, FTP, SMTP, etc.

---

## 📊 Use Statistics Menu

- `Statistics → Protocol Hierarchy` — See protocol breakdown
- `Statistics → Conversations` — View IP pairs and traffic volume
- `Statistics → Endpoints` — See active devices

---

## 🧪 Decode Payloads

- Use `Export Packet Bytes` to extract payload
- Decode with [CyberChef](https://gchq.github.io/CyberChef/)
- Useful for base64, hex, XOR, and obfuscated data

---

## 💾 Save Your Captures

- Save `.pcapng` files for later analysis
- Use `File → Export Specified Packets` to trim large captures
- Great for documenting lab results or sharing with peers

---

## 🧰 Customize Layout

- Rearrange panes: Packet List, Details, Bytes
- Use `Ctrl + H` to toggle details pane
- Set default columns via `Preferences → Appearance`

---


Maintained by **Lets Learn -08**  
🎓 BCA Student | Cybersecurity Enthusiast | Nullclass Intern
