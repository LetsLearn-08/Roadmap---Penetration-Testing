# 🧪 Lab: ARP Resolution

## 🎯 Objective
Capture and analyze **ARP (Address Resolution Protocol)** traffic in Wireshark to understand how IP addresses are mapped to MAC addresses on a local network.

---

## 🛠 Setup

- Environment: VirtualBox lab  
- Target: Metasploitable2 or any host in the same subnet  
- Tool: Wireshark (latest version)  
- Command line: `ping` or `arp -a` to trigger ARP lookups  

---

## 🚀 Steps

1. **Start Wireshark** and select your active network interface.  
2. **Clear ARP cache** (optional, to force resolution):  
   - Linux: `sudo ip -s -s neigh flush all`  
   - Windows: `arp -d *`  
3. **Run a ping command** to a host in your subnet:
 ```bash
   ping 192.168.1.10
   ```
4. **Apply a display filter in Wireshark:**
```
arp
```
5. Observe the captured packets:
  - ARP Request: Who has 192.168.1.10? Tell 192.168.1.5
  - ARP Reply: 192.168.1.10 is at 00:0c:29:ab:cd:ef

## 🔍 What to Look For

- Opcode: Request (1) vs Reply (2)
- Sender MAC/IP: The host asking for resolution
- Target MAC/IP: The host being resolved
- Broadcast behavior: Requests are broadcast, replies are unicast

## 📸 Documentation

- Screenshot: ARP request packet details.
- Screenshot: ARP reply showing resolved MAC address.
- Notes: IP ↔ MAC mapping, broadcast vs unicast behavior.

## ✅ Outcome

- By completing this lab, you will:
- Understand how ARP resolves IP addresses to MAC addresses.
- Learn to filter and analyze ARP traffic in Wireshark.
- Build a foundation for detecting ARP spoofing or anomalies in future labs.
