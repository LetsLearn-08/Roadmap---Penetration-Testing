# Host-Only Networking Setup

## 🌐 Goal
Enable isolated communication between Kali Linux and Metasploitable2 VMs.

## 🔧 Steps
1. **Create Host-Only Adapter**:
   - VirtualBox → File → Host Network Manager
   - Create new adapter (e.g., `vboxnet0`)
   - Set IP: `192.168.56.1`, Subnet: `255.255.255.0`

2. **Attach to VMs**:
   - Kali → Settings → Network → Adapter 2 → Host-only Adapter (`vboxnet0`)
   - Metasploitable → Same setup

3. **Check IPs**:
   - Kali: `ip a` → should be `192.168.56.x`
   - Metasploitable: `ifconfig` → same subnet

4. **Test Connectivity**:
   ```bash
   ping 192.168.56.x  # From Kali to Metasploitable
