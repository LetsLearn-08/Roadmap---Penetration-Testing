# 🔍 Wireshark Filters Cheatsheet

Wireshark filters help you narrow down captured traffic to focus on specific protocols, IPs, ports, or behaviors. This cheatsheet covers both **capture filters** (set before starting capture) and **display filters** (used after capture).

---

## 🎯 Capture Filters

Capture filters are applied before starting the capture. They use **libpcap syntax** and are more limited than display filters.

| Filter | Description |
|--------|-------------|
| `port 80` | Capture only HTTP traffic |
| `host 192.168.1.1` | Capture traffic to/from a specific IP |
| `net 192.168.1.0/24` | Capture traffic in a subnet |
| `tcp` | Capture only TCP packets |
| `udp` | Capture only UDP packets |
| `icmp` | Capture ping (ICMP) traffic |
| `tcp port 443` | Capture HTTPS traffic |
| `src port 53` | Capture DNS responses |
| `dst port 53` | Capture DNS queries |

port 80 or port 443

---

## 🧪 Display Filters

Display filters are applied after capture and use **Wireshark’s own syntax**. They are more powerful and flexible.

| Filter | Description |
|--------|-------------|
| `ip.addr == 192.168.1.1` | Show packets to/from IP |
| `tcp.port == 80` | Show HTTP traffic |
| `http.request` | Show HTTP requests |
| `dns` | Show DNS packets |
| `icmp` | Show ping packets |
| `tcp.flags.syn == 1` | Show TCP SYN packets |
| `tcp.flags.fin == 1` | Show TCP FIN packets |
| `tcp contains "GET"` | Show packets with HTTP GET |
| `frame contains "password"` | Show packets with the word "password" |
| `tcp.analysis.retransmission` | Show retransmitted packets |
| `ssl.handshake` | Show TLS/SSL handshake packets |

---


## 🧠 Tips

- Use `and`, `or`, `not` to combine filters
- Use `==` for exact match, `contains` for partial match
- Right-click a packet → “Apply as Filter” for quick filtering
- Save filters for reuse in `.wsf` profiles

---

## 📚 Learn More

- [Wireshark Display Filter Reference](https://wiki.wireshark.org/DisplayFilters)
- [Wireshark Capture Filter Reference](https://wiki.wireshark.org/CaptureFilters)

---

Maintained by **Lets learn -08 **  
🎓 BCA Student | Cybersecurity Enthusiast | Nullclass Intern
