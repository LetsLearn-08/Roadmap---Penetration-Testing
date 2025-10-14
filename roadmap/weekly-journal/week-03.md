> 📄 View-only content. Licensed under terms in [LICENSE-NOTES.md](../LICENSE-NOTES.md).
>
> # 🛡️ Networking  Fundamentals — Part 1

## 1. Models & Fundamentals

### OSI vs TCP/IP

- **OSI Layers (7)**: Application, Presentation, Session, Transport, Network, Data Link, Physical  
  Useful for mapping functions.
- **TCP/IP Layers (4)**:  
  - Application (apps + protocols like HTTP/DNS)  
  - Transport (TCP/UDP)  
  - Internet (IP)  
  - Link (Ethernet/Wi‑Fi)

**Pentester Mapping**:
- Reconnaissance: Application & Network layers  
- Exploitation: Link & Transport (e.g., ARP, TCP flags)  
- Pivoting: Network & Transport layers

### Encapsulation


Track headers top-down when analyzing captures.

### State vs Stateless

- **TCP**: Connection-oriented (stateful handshake, sequence/ACK)
- **UDP**: Connectionless (stateless)

**Pentest Tip**: Stateful firewalls & IDS/IPS track TCP state. Crafting packets that violate state machines can bypass naive systems.

---

## 2. Ethernet & Data Link

### Ethernet Frame Structure

| Field            | Size       |
|------------------|------------|
| Preamble         | 7 bytes    |
| SFD              | 1 byte     |
| Destination MAC  | 6 bytes    |
| Source MAC       | 6 bytes    |
| EtherType        | 2 bytes    |
| Payload          | 46–1500 B  |
| FCS              | 4 bytes    |

**EtherType Values**:
- `0x0800` = IPv4  
- `0x86DD` = IPv6  
- `0x0806` = ARP

### MAC Addressing

- 48-bit address (e.g., `00:11:22:aa:bb:cc`)
- First 24 bits = vendor (OUI)
- Types: Unicast, Multicast, Broadcast (`ff:ff:ff:ff:ff:ff`)

### VLANs & 802.1Q

- VLAN tag: 4 bytes after source MAC  
  - TPID: `0x8100`  
  - TCI: 12-bit VLAN ID

**VLAN Hopping**:
- Misconfigured trunking/native VLANs → cross-VLAN traffic  
- Defense: disable unused trunking, restrict native VLAN

### ARP

- Request: "Who has IP X?"  
- Reply: Contains MAC

**Pentest Tip**: ARP is unauthenticated → cache poisoning risks.  
Look for gratuitous ARP anomalies.  
Defense: static ARP entries, dynamic ARP inspection.

---

## 3. IPv4 Internals

### IPv4 Header Fields

- Version, IHL, DSCP, Total Length, Identification  
- Flags (DF/MF), Fragment Offset, TTL, Protocol  
- Header Checksum, Source/Dest IP, Options

### IP Fragmentation

- MTU = 1500  
- IP header = 20 bytes  
- TCP header = 20 bytes  
- Max payload per fragment = `1500 − 14 − 20 − 20 = 1446 bytes`

**DF Set**: Fragmentation denied → ICMP "Fragmentation needed"  
Used in Path MTU Discovery

**Pentest Tip**: Overlapping fragments confuse IDS/IPS.  
Analyze reassembly behavior.

### TTL

- Decrements per router hop  
- Used in `traceroute`  
- TTL anomalies → NAT, virtualization, injection

### IP Options

- Rare in normal traffic (e.g., Record Route)  
- Suspicious use → scanning/evasion

---

## 4. IPv6 Essentials

### Address Types

- Global Unicast  
- Link-local (`fe80::/10`)  
- Unique Local (`fc00::/7`)  
- Multicast (`ff00::/8`)

### NDP (Neighbor Discovery Protocol)

- Replaces ARP (ICMPv6)  
- Vulnerable to spoofing if unsecured

### Extension Headers

- Hop-by-hop, Routing, Fragment  
- Can be abused for evasion  
- Some devices drop unexpected headers

---

## 5. Subnetting (Worked Examples)

### Example 1 — `/26` Subnet

IP: `192.168.10.77`  
Mask: `/26` → `255.255.255.192`  
Host bits: 6

**Network**: `192.168.10.64`  
**Broadcast**: `192.168.10.127`  
**Usable Range**: `192.168.10.65` to `192.168.10.126`

### Example 2 — `/30` Subnet

- Host bits: 2 → `2^2 − 2 = 2` usable addresses  
- Ideal for point-to-point links

**Pentest Tip**:  
Routing boundaries help identify pivot points and scanning scope.  
Misconfigured subnets may leak internals.

---

## 6. TCP Deep Dive

### TCP Header Fields

- Src/Dst Port, Seq, Ack  
- Flags: `NS, CWR, ECE, URG, ACK, PSH, RST, SYN, FIN`  
- Window Size, Checksum, Options (MSS, SACK, Timestamps)

### Handshake & Termination

- **Three-way**: `SYN → SYN/ACK → ACK`  
- **Termination**: `FIN/ACK`, or `RST` for abrupt close

### Flow Control

- Window size = how much data receiver accepts  
- Scaling option extends beyond `65,535`

### Scanning Logic

- **SYN Scan**: Open → SYN/ACK, Closed → RST  
- **FIN/NULL/Xmas Scans**: Exploit OS stack behavior

### Sequence Numbers & ACKs

- Cumulative ACKs  
- Odd flags (e.g., `SYN+FIN`), invalid checksums, hijacking indicators

**Passive Fingerprinting**:
- TTL, window size, TCP options patterns

---

## 7. UDP & ICMP

### UDP

- Header: Src/Dst Port, Length, Checksum  
- No handshake (stateless)

**Pentest Tip**:  
Used in DNS, SNMP, NTP.  
UDP scans are noisy due to ICMP rate-limiting.

### ICMP

- Types:  
  - Echo Request/Reply (8/0)  
  - Dest Unreachable (3)  
  - Time Exceeded (11)  
  - Redirect (5)

**Pentest Tip**:  
Used for ping sweeps, traceroute, covert channels.  
Often restricted by defenders.

---
## "The network isn't just a wire; it's the entire battlefield.
Mastering its fundamentals means you know where to build the strongest defenses and spot the subtlest intrusions.
Keep exploring, keep experimenting, and never stop learning. The terminal is your canvas—paint boldly."

 # STAY TUNED TILL NEXT WEEK..@LetsLearn-08
