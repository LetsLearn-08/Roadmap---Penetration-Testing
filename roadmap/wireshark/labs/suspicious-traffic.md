# 🧪 Lab: Suspicious Traffic (Port Scans & Anomalies)

## 🎯 Objective
Capture and analyze **suspicious traffic patterns** such as port scans, malformed packets, or unusual flows using Wireshark.  
This lab builds awareness of how attackers probe networks and how defenders can spot anomalies.

---

## 🛠 Setup

- Environment: VirtualBox lab  
- Target: Metasploitable2 (or any test VM)  
- Tool: Wireshark (latest version)  
- Optional: Use **Nmap** to generate controlled scan traffic for analysis  

---

## 🚀 Steps

1. **Start Wireshark** and select your active network interface.  
2. **Generate suspicious traffic** (controlled lab only):  
   ```bash
   nmap -sS -p 1-100 192.168.1.10
   ```
3. Apply display filters in Wireshark:

```
tcp.flags.syn == 1 and tcp.flags.ack == 0
(Shows SYN packets typical of scans)

tcp.analysis.retransmission
(Highlights retransmissions or anomalies)
```

4. Observe the captured packets:

- Repeated SYN packets without replies
- Unusual frequency or sequence of requests
- Traffic targeting closed ports

## 🔍 What to Look For

- Patterns of scanning: Many SYN packets to sequential ports
- Unanswered requests: SYN packets without SYN‑ACK replies
- Timing anomalies: Very fast bursts of packets
- Protocol misuse: Unexpected traffic types (e.g., ICMP floods)

## 📸 Documentation

- Screenshot: SYN scan packet list
- Screenshot: Filtered view showing suspicious traffic
- Notes: Ports targeted, frequency of requests, anomalies observed

## ✅ Outcome

By completing this lab, you will:

- ✅ Recognize common signs of port scans and suspicious activity
- ✅ Learn to apply filters that highlight anomalies
- ✅ Build a foundation for detecting malicious traffic in real environments
