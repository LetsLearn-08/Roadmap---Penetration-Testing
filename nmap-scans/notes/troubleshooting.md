# Nmap Troubleshooting

A quick reference for fixing common `nmap` issues. Paste this into your repo.

---

## 🔧 Common Issues & Fixes

### ❌ "Failed to open device eth0 (Permission denied)"
- **Fix:** Run with `sudo`.

```bash
sudo nmap -sS <target>
```
### ❌ "Host seems down. If it is really up, try -Pn"

Fix: ICMP blocked. Use -Pn to skip ping check.
```
nmap -Pn <target>
```
### ❌ All ports show as "filtered"

Fix 1: Try TCP connect scan (-sT).

Fix 2: Target may have a firewall.
```
nmap -sT <target>
```
### ❌ "Nmap done: 0 IP addresses (0 hosts up)"

Fix: ICMP likely blocked. Use -Pn, check network/firewall.
```
nmap -Pn <target>
```
 ### ❌ Service detection shows "unknown"

Fix: Increase version intensity.
```
nmap -sV --version-intensity 9 <target>
````
 ## 🔍 Debugging Tips
 
- Show packet-level details
 ```
sudo nmap --packet-trace -p 80 <target>
```
- Capture traffic with tcpdump
```
sudo tcpdump -i eth0 host <target>
```

## ✅ Scan Examples

- Basic scan (top ports)
```
nmap <target>
```
- Full TCP scan (all 65535 ports)
```
sudo nmap -p- -T4 <target>
```
- Scan with version & OS detection
```
sudo nmap -A <target>
```
- UDP scan
 ```
sudo nmap -sU -p 53,123,161 <target>
```
## 🧪 NSE Script Debugging

- Run a script with trace
```
sudo nmap --script http-title --script-trace <target>
```

- Set script arguments
```
sudo nmap --script http-brute --script-args userdb=users.txt,passdb=passes.txt <target>
```
## 🛡 Firewall Bypass Tips (use only if authorized)

- Use -Pn to avoid ping detection.
- Try -T1 or --scan-delay to slow down.
- Use -sT instead of -sS if SYN is blocked.

## ✅ Checklist

- Use sudo when needed
- Try -Pn if host seems down
- Use -sT if firewall blocks SYN
- Use --packet-trace for low-level debug
- Check for ICMP/firewall rules blocking scan
- Capture with tcpdump if needed
