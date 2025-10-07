> 📄 View-only content. Licensed under terms in [LICENSE-NOTES.md](../LICENSE-NOTES.md).
>
> # 🛡️ Networking  Fundamentals — Part 2
>
> ### IT IS THE CONTINUATION OF NOTES FOR NETWORKING FUNDAMENTALS, AND ADDITIONAL INFORMATION ABOUT "WIRESHARK"

## 8. Common Application Protocols

### DNS (UDP/TCP 53)

- Record types: A, AAAA, MX, CNAME, TXT, NS, SOA
- DNS over TCP used for zone transfers (AXFR)
- DNSSEC prevents tampering
- DNS rebinding bypasses browser same-origin policies

**Pentest Tips**:
- Check for open recursive resolvers
- Zone transfers allowed to external IPs
- Unusual TXT records

### HTTP / HTTPS

- HTTP: plaintext headers, cookies
- HTTPS/TLS: metadata leaks via SNI, ALPN
- TLS handshake: ClientHello → ServerHello → Certificate → Key Exchange → Finished

**Pentest Tips**:
- TLS downgrade attacks
- Weak cipher suites
- Misconfigured TLS terminators
- HSTS misconfigurations

### SMB (445), NetBIOS (137–139)

- File shares, NTLMv1/v2, Kerberos
- Legacy protocols (SMBv1) are risky

**Pentest Tips**:
- Anonymous shares
- SMB signing disabled

### LDAP (389 / 636)

- Directory queries
- Anonymous bind may expose sensitive attributes

### SNMP (161/162)

- v1/v2c: plaintext community strings (`public`, `private`)
- v3: encryption + authentication

### SMTP / POP3 / IMAP

- Open relays
- Banner leaks
- VRFY/EXPN for user enumeration

### RDP (3389)

- Remote desktop
- Check for NLA and gateway protections

### Databases

- MySQL (3306), MSSQL (1433), PostgreSQL (5432)
- Banners may leak version info

### HTTP/2 & HTTP/3 (QUIC)

- HTTP/2: multiplexed streams, HPACK compression
- QUIC: UDP-based, encrypted handshake

---

## 9. Routing & Switching Internals

### Routing Protocols

- **BGP**: susceptible to hijacking/prefix leaks
- **OSPF**: LSA poisoning, spoofed LSAs

### ACLs & Route Filtering

- ACLs control subnet communication
- Watch for asymmetric routing, split horizon issues

### NAT & PAT

- NAT hides internal IPs
- PAT maps multiple internal IPs to one external port

**Pentest Tip**: Hairpin NAT may allow internal access via external IP

---

## 10. Wireless (Wi‑Fi) Deep Points

### 802.11 Frames

- Management, control, data frames
- Beacons include SSID, supported rates

### Authentication vs Encryption

- WEP (broken), WPA/WPA2 (PSK/Enterprise), WPA3 (SAE/OWE)

### Rogue AP & Evil Twin

- Rogue APs intercept auth or push malicious content

### Enterprise (802.1X)

- EAP methods: PEAP, EAP-TLS (strongest)

**Pentest Focus**:
- Weak PSKs
- Open management frames
- Misconfigured Enterprise setups

---

## 11. Network Security Devices

### Firewalls

- Stateless vs Stateful
- DPI inspects payloads

### IDS/IPS

- IDS: detects
- IPS: blocks
- Signature-based & anomaly-based

**Evasion**: Fragmentation, timing, encryption

### Proxies & Load Balancers

- Reverse proxies terminate TLS
- Misconfigurations may leak backend IPs or headers

---

## 12. Packet Capture & Analysis

### Capture Tips

- Use SPAN/mirror ports or host-based capture
- Monitor mode required for 802.11 management frames

### Filters

- **Capture Filter** (libpcap/BPF): `host 10.0.0.5`
- **Display Filter** (Wireshark): `ip.addr==10.0.0.5 && tcp.port==80`

### Key Wireshark Filters


tcp.flags.syn == 1 && tcp.flags.ack == 0  # SYN packets
arp                                         # ARP traffic
http.request                                # HTTP requests

# 🧪 Wireshark Cheat Sheet for Pentesters

A practical guide to using Wireshark for packet capture, protocol analysis, and network reconnaissance.

---

## 📦 What Is Wireshark?

Wireshark is a powerful packet analyzer used to inspect network traffic in real time or from saved `.pcap` files. It helps visualize protocols, detect anomalies, and understand packet-level behavior.

---

## 🛠️ Setup & Capture

### Interface Selection
- Choose the correct interface (e.g., `eth0`, `wlan0`)
- Enable **promiscuous mode** to capture all traffic
- For Wi‑Fi: enable **monitor mode** to capture 802.11 management frames

### Starting a Capture
- Use capture filters to limit stored data
- Save `.pcap` files for later analysis

---

## 🔍 Filters

### Capture Filters (libpcap/BPF)
Applied before capture to reduce noise:

host 192.168.1.10
port 80
net 10.0.0.0/24
tcp
udp

## 🧵 Useful Display Filters (Quick Reference)

dns                             # All DNS traffic
udp.port == 53                  # DNS over UDP
tcp.port == 53                  # DNS over TCP
http.request                    # HTTP requests
tcp.flags.syn == 1 && tcp.flags.ack == 0   # SYN packets
icmp                            # ICMP messages
arp                             # ARP traffic
ip.addr == 10.0.0.5 && tcp.port == 80      # Specific host and port

# 📡 Protocol Analysis — Pentester’s Reference

A breakdown of common application-layer protocols, what to inspect, and why they matter during reconnaissance and exploitation.

---

## 🧠 DNS (UDP/TCP 53)

### Core Features
- Query/response model
- Common record types: A, AAAA, MX, CNAME, TXT, NS, SOA
- DNS over TCP used for large responses or zone transfers (AXFR)

### Security Considerations
- DNS cache poisoning risks
- DNSSEC prevents tampering via cryptographic signing
- DNS rebinding can bypass browser same-origin policies

### Pentest Notes
- Check for open recursive resolvers
- Zone transfers allowed to external IPs
- Unusual TXT records may indicate tunneling or exfiltration

---

## 🌐 HTTP / HTTPS

### Core Features
- HTTP is plaintext — inspect headers, cookies, and methods
- HTTPS uses TLS to encrypt payloads but leaks metadata (SNI, ALPN)

### TLS Handshake Breakdown
- ClientHello (ciphers, extensions)
- ServerHello
- Certificate
- Key Exchange
- Finished

### Pentest Notes
- TLS downgrade attacks
- Weak cipher suites
- Expired or self-signed certificates
- Misconfigured TLS terminators
- HSTS misconfiguration

---

## 🗂️ SMB (445) & NetBIOS (137–139)

### Core Features
- File sharing and authentication (NTLMv1/v2, Kerberos)

### Pentest Notes
- Anonymous SMB shares
- SMB signing disabled
- Legacy protocols (SMBv1) still enabled

---

## 📇 LDAP (389 / 636)

### Core Features
- Directory queries, often used for authentication

### Pentest Notes
- Sensitive attributes may be exposed if anonymous bind is allowed

---

## 📡 SNMP (161/162)

### Core Features
- v1/v2c use plaintext community strings (like passwords)
- Common defaults: `public`, `private`
- SNMPv3 adds encryption and authentication

### Pentest Notes
- Default strings can leak device config
- SNMPv3 preferred for secure environments

---

## ✉️ SMTP (25), POP3/IMAP

### Core Features
- Email protocols for sending and receiving

### Pentest Notes
- Open relays allow abuse
- Banner leaks reveal software versions
- VRFY/EXPN can be used for user enumeration

---

## 🖥️ RDP (3389)

### Core Features
- Remote desktop access

### Pentest Notes
- Check for network-level authentication (NLA)
- Gateway protections should be enforced

---

## 🗃️ Databases

### Ports
- MySQL: 3306
- MSSQL: 1433
- PostgreSQL: 5432

### Pentest Notes
- Exposed DBs may leak sensitive info
- Banners often reveal version info — patching is critical

---

## 🚀 Emerging Protocols

### HTTP/2
- Multiplexes streams over one TCP connection
- Uses HPACK header compression

**Caution**: HPACK compression has historical side-channel risks (CRIME-like)

### HTTP/3 (QUIC)
- Uses UDP
- Encrypts much of the handshake data

**Impact**: Makes packet analysis harder — metadata visibility reduced

---

## "The network isn't just a wire; it's the entire battlefield.
Mastering its fundamentals means you know where to build the strongest defenses and spot the subtlest intrusions.
Keep exploring, keep experimenting, and never stop learning. The terminal is your canvas—paint boldly."

 # STAY TUNED TILL NEXT WEEK..@LetsLearn-08

