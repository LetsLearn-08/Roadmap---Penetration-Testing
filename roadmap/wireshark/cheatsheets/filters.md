# 📘 Cheatsheet: Wireshark Filters

## 🎯 Objective
Quick reference for commonly used **capture filters** and **display filters** in Wireshark.

---

## 🛠 Capture Filters
*(Applied before starting a capture — limits what packets are recorded)*

- `host 192.168.1.10` → Capture traffic to/from a specific host  
- `net 192.168.1.0/24` → Capture traffic in a subnet  
- `tcp port 80` → Capture only HTTP traffic  
- `udp port 53` → Capture only DNS queries/responses  
- `icmp` → Capture ping (ICMP) traffic  
- `port 443` → Capture HTTPS traffic  

---

## 🔍 Display Filters
*(Applied after capture — shows only matching packets)*

- `ip.addr == 192.168.1.10` → Show traffic involving a specific IP  
- `tcp.port == 22` → Show SSH traffic  
- `udp.port == 53` → Show DNS traffic  
- `http.request` → Show HTTP requests only  
- `http.response` → Show HTTP responses only  
- `icmp` → Show ping traffic  
- `arp` → Show ARP requests/replies  
- `tcp.flags.syn == 1 and tcp.flags.ack == 0` → Show SYN packets (useful for scans)  

---

## ⚡ Productivity Tips

- Use **coloring rules** to highlight protocols (TCP, UDP, ICMP).  
- Combine filters with `and`, `or`, `not`:  
  - `ip.src == 192.168.1.5 and tcp.port == 80`  
- Save frequently used filters in **Wireshark’s filter toolbar** for quick access.  

---

## ✅ Outcome
By using these filters, you can:  
- ✅ Narrow down captures to relevant traffic  
- ✅ Quickly analyze specific protocols or hosts  
- ✅ Detect anomalies like scans or suspicious flows
