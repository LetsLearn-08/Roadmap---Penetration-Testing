# 🧪 Lab: Ping Test (ICMP)

## 🎯 Objective
Capture and analyze **ICMP echo requests and replies** using Wireshark to understand how the `ping` command works at the packet level.

---

## 🛠 Setup

- Environment: VirtualBox lab  
- Target: Metasploitable2 or any reachable host (e.g., `google.com`)  
- Tool: Wireshark (latest version)  

---


## 🚀 Steps

1. **Start Wireshark** and select your active network interface.  
2. **Run a ping command** in terminal:  
```bash
   ping -c 4 google.com
```
(On Windows: ping google.com)
4. **Apply a display filter in Wireshark:**
```
icmp
```
4. **Observe the captured packets:**

- Echo request (from your machine → target)
- Echo reply (from target → your machine)

## 🔍 What to Look For

- Packet details:
  - Type: Echo Request (Type 8) / Echo Reply (Type 0)
  - Identifier & Sequence number fields
  - TTL (Time To Live) values
- Round‑trip time: Compare timestamps between request and reply.
- Patterns: Notice how sequence numbers increment with each ping.

## 📸 Documentation

- Screenshot: ICMP packet list with filter applied.
- Screenshot: Detailed view of Echo Request and Echo Reply.
- Notes: Round‑trip times, sequence numbers, TTL values.

## ✅ Outcome

By completing this lab, you will:
- Understand how ICMP is used for connectivity testing.
- Learn to filter and analyze ping traffic in Wireshark.
- Build a foundation for detecting ICMP‑based scans or anomalies in future labs.
