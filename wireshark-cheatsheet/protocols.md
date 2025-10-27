# 📡 Protocols Cheatsheet

This guide breaks down the most common protocols you'll encounter in Wireshark. Each section includes what the protocol does, how it appears in packet captures, and useful filters to isolate it.

---

## 🔁 TCP (Transmission Control Protocol)

- **Purpose**: Reliable, connection-oriented communication (e.g., web browsing, file transfers)
- **Key Features**:
  - 3-way handshake: SYN → SYN-ACK → ACK
  - Sequence and acknowledgment numbers
  - Flags: SYN, ACK, FIN, RST
- **Filters**:
  - `tcp` — All TCP traffic
  - `tcp.flags.syn == 1` — SYN packets (start of handshake)
  - `tcp.port == 80` — HTTP over TCP

---

## 🌐 HTTP (Hypertext Transfer Protocol)

- **Purpose**: Web communication (GET, POST, etc.)
- **Key Features**:
  - Request methods: GET, POST, PUT
  - Headers: Host, User-Agent, Cookie
  - Payload: HTML, JSON, etc.
- **Filters**:
  - `http` — All HTTP traffic
  - `http.request` — Only HTTP requests
  - `http contains "login"` — Requests containing "login"

---

## 📨 DNS (Domain Name System)

- **Purpose**: Resolves domain names to IP addresses
- **Key Features**:
  - Query types: A, AAAA, MX, CNAME
  - Response codes: NOERROR, NXDOMAIN
- **Filters**:
  - `dns` — All DNS traffic
  - `dns.qry.name == "example.com"` — Queries for a specific domain
  - `udp.port == 53` — DNS over UDP

---

## 📶 ICMP (Internet Control Message Protocol)

- **Purpose**: Network diagnostics (ping, unreachable messages)
- **Key Features**:
  - Echo request/reply
  - TTL exceeded
- **Filters**:
  - `icmp` — All ICMP traffic
  - `icmp.type == 8` — Echo request
  - `icmp.type == 0` — Echo reply

---

## 🔐 TLS/SSL (Transport Layer Security)

- **Purpose**: Encrypts data over HTTPS, FTPS, etc.
- **Key Features**:
  - Handshake: Client Hello, Server Hello
  - Certificate exchange
- **Filters**:
  - `ssl.handshake` — TLS handshake packets
  - `tcp.port == 443` — HTTPS traffic

---



Maintained by **Lets Learn -08**  
🎓 BCA Student | Cybersecurity Enthusiast | Nullclass Intern
