> 📄 View-only content. Licensed under terms in [LICENSE-NOTES.md](../LICENSE-NOTES.md).

# 🐧 Kali Linux Notes

## 1. Basics

- **Binaries**: Executable files like `ps`, `cat`, `ls`, `cd`
- **Directory**: Folder structure for organizing files
- **Home**: Each user has their own `/home` directory
- **Root**: Superuser account with full privileges
- **Script**: Instructions to automate tasks
- **Shell**: Command-line interface
- **Change Password**: Use `passwd`
- **Linux File System**: Organized under `/`, treats everything as a file

### Key Directories

- `/root`: Root user’s home
- `/etc`: Configuration files
- `/home`: User directories
- `/mnt`: Mounted filesystems
- `/media`: Mounted devices
- `/bin`: Application binaries
- `/lib`: Libraries

---

## 2. Navigation & User Info

- `pwd`: Print working directory
- `whoami`: Show current user
- `cd`: Change directory

---

## 3. Viewing Contents

- `ls`: List directory contents
- `ls -l`: Detailed listing
- `ls -la`: Show hidden files

---

## 4. Help & Manual

- `help`: Quick info on built-in commands
- `man`: Manual pages (e.g. `man aircrack-ng`)

---

## 5. File Location & Search

- `whereis aircrack-ng`: Locate binaries, source, and manuals
- `find /home -type f -name "file.txt"`: Search files
- `grep`: Filter output or search text

---

## 6. Processes

- `ps`: Show running processes
- `ps aux`: Show all processes
- `ps aux | grep keyword`: Search for specific process

---

## 7. Creating & Managing Files

- `cat > hackingskill`: Create file
- `cat >> hackingskill`: Append to file
- `touch newfile`: Create empty file
- `mkdir newdirectory`: Create directory
- `cd newdirectory`: Enter directory
- `locate aircrack-ng`: Quickly find files

---

## 8. Environment & File Operations

- `which aircrack-ng`: Show command path
- `mv file newlocation/`: Move or rename file
- `rm newfile`: Remove file
- `rmdir newdirectory`: Remove directory

---

## 9. Text Manipulation

- `head /etc/snort/snort.conf`: View beginning of file
- `tail /etc/snort/snort.conf`: View end of file
- `nl filename`: Number lines
- `cat /etc/snort/snort.conf | grep output`: Filter lines with keyword
- `more /etc/snort/snort.conf`: View file page-by-page
- `less /etc/snort/snort.conf`: Scroll and filter file

---

## 10. Networking

### ifconfig

- View and configure network interface settings
- `eth0`: Active interface
  - `inet`: IPv4 address
  - `netmask`: Subnet mask
  - `broadcast`: Broadcast address
  - `RX/TX packets`: Data stats
  - `ether`: MAC address
- `lo`: Loopback interface

### When to Use ifconfig

- Check IP address
- Diagnose connectivity issues
- Verify interface status
- Troubleshoot with packet stats

---

## 11. Modern Networking Tools

- `ip addr`: Replacement for `ifconfig`
- `iwconfig`: Wireless adapter info

---

## 12. Wireless Networking

- **Wireless Adapter**: Hardware that connects to Wi-Fi networks
- `iwconfig`: Shows IP, MAC, and wireless details

---

## 13. Changing Network Info

- Use GUI: Network Settings → IPv4/IPv6
- Use terminal: Edit `/etc/network/interfaces`
- Set static IPs, DNS, gateways for secure connections

---

## 14. DNS Manipulation

- Edit `/etc/hosts` for local overrides
- Use tools: `dig`, `nslookup`, `dnsspoof`
- Useful for spoofing and ethical hacking

---

## 15. Mapping IP Addresses

- Use `nmap` or `netdiscover` to scan network
- Example: `sudo netdiscover -r 192.168.1.0/24`
- Lists active hosts, IPs, MACs, open ports

---

## 16. Software Management with APT

- `sudo apt update`: Refresh package list
- `sudo apt install <package>`: Install software
- `sudo apt upgrade`: Update all packages
- `sudo apt remove <package>`: Uninstall software

---

## 17. File & Directory Permissions

- `chmod`: Change permissions
- `chown`: Change ownership
- `ls -l`: View permissions

### Examples

- `chmod u+x script.sh`: Add execute permission
- `chown user:group file`: Change ownership

---

## 18. Root Execute Permission

- `sudo chmod u+s /path/to/toolbit`: Setuid for root access

---

## 19. Netstat

- Monitor network connections
- Syntax: `netstat [options]`

### Common Options

- `-a`: Show all connections
- `-n`: Numeric addresses
- `-o`: Show PID
- `-b`: Show executable (Windows only)
- `-r`: Routing table
- `-s`: Protocol stats

---

## 20. ss (Socket Statistics)

- Faster alternative to netstat
- Syntax: `ss [options]`

### Common Options

- `-t`: TCP sockets
- `-u`: UDP sockets
- `-l`: Listening sockets
- `-a`: All sockets
- `-n`: Numeric addresses
- `-p`: Show process
- `-s`: Summary stats

---

## 21. Ping

- Test network connectivity
- Syntax: `ping [destination]`

### How It Works

- Sends ICMP Echo Request
- Waits for Echo Reply
- Measures round-trip time (RTT)

---

## 22. Traceroute

- Trace path to destination
- Syntax: `traceroute [hostname or IP]`

### Purpose

- Shows each hop (router)
- Measures latency
- Diagnoses delays or failures

## Mastering Kali Linux isn’t just about commands—it’s about understanding the system, thinking like a hacker, and staying curious. These notes are your launchpad.
Keep exploring, keep experimenting, and never stop learning. The terminal is your canvas—paint boldly.
 

 # STAY TUNED TILL NEXT WEEK..@LetsLearn-08
