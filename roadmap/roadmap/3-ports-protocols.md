
ITS JUST AN OVERVIEW OF THE PORTS AND PROTOCALS-- 

FOR DETAILED NOTES, SYNTAX and EXAMPLES @ CHECK MY WEEKLY PROGRESS

# 🛠️ Ports and Protocols – Pentesting Essentials

Understanding ports and protocols is **fundamental for any penetration tester**. This guide provides a concise overview of the most important ones, including what they do and why they matter during security assessments.

---

## 📘 What Are Ports and Protocols?

- **Protocol**: A set of rules for transmitting data between devices (e.g., HTTP, FTP, SSH).
- **Port**: A communication endpoint. Each protocol typically operates on a specific port number (e.g., HTTP = Port 80).

---

## 📋 Common Ports and Protocols for Pentesting

| Port | Protocol | Description | Pentesting Relevance |
|------|----------|-------------|------------------------|
| 21   | FTP      | File Transfer Protocol (Unencrypted) | Check for anonymous login, credential leaks |
| 22   | SSH      | Secure Shell | Target for brute force, weak keys, or outdated versions |
| 23   | Telnet   | Unencrypted remote login | Legacy systems, sniffable credentials |
| 25   | SMTP     | Mail Transfer | Check for open relays, spoofing |
| 53   | DNS      | Domain Name System | DNS tunneling, zone transfers |
| 80   | HTTP     | Web traffic | Test for web vulnerabilities (e.g., XSS, SQLi) |
| 110  | POP3     | Email retrieval (Unencrypted) | Weak auth, credential harvesting |
| 139  | NetBIOS  | Windows file/printer sharing | Enumeration, SMB relay attacks |
| 143  | IMAP     | Email protocol | Auth testing, email harvesting |
| 443  | HTTPS    | Secure HTTP | SSL/TLS testing, web app pentesting |
| 445  | SMB      | Windows shares | EternalBlue, SMB relay, credential theft |
| 3306 | MySQL    | Database service | Brute-force, SQL injection |
| 3389 | RDP      | Remote Desktop Protocol | Brute-force, remote access vulnerabilities |
| 8080 | HTTP Alt | Alternative HTTP port | Often used for proxies, web apps |

---

## 🎯 Why This Matters in Pentesting

- 🔍 **Reconnaissance**: Knowing common ports helps identify services during scans (e.g., with `nmap`, `masscan`).
- 🧪 **Vulnerability Assessment**: Each open port could expose a vulnerable service.
- 🧰 **Exploitation**: Exploits often target specific services and versions.
- 🚪 **Persistence**: Compromised services can be used as backdoors for re-entry.

---

## 🧠 Tools to Practice

- `nmap` – Network scanning and service enumeration  
- `netcat` – Banner grabbing and manual testing  
- `wireshark` – Protocol analysis and traffic sniffing  
- `masscan` – Fast port scanning  
- `metasploit` – Exploitation framework  

---

## 📌 Pro Tips

- Always scan both **TCP** and **UDP** ports (`nmap -sS -sU`).
- Use version detection: `nmap -sV`.
- Don’t forget about **uncommon ports** (services can run anywhere).
- Automate with scripts, but validate manually when needed.

---

## ✅ Learn More

- [IANA Port Assignments](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
- [Nmap Book](https://nmap.org/book/)
- [HackTricks – Pentesting Cheatsheet](https://book.hacktricks.xyz/)

---

> # 💡 **Tip**: Ports are doors. Protocols are languages. As a pentester, your job is to find the open doors, listen to the conversations, and exploit the weak ones.
>
> Lets meet at the PACKET ANALYSIS ...

