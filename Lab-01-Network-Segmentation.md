# Lab 01: Secure Network Segmentation

### 🎯 Objective
To implement VLAN-based segmentation and secure departmental traffic using Extended Access Control Lists (ACLs) to prevent unauthorized lateral movement.

### 🛠 Environment
* **Platform**: GNS3
* **Hardware**: Cisco 3725 Router, Cisco Catalyst Switch
* **Protocols**: 802.1Q (Trunking), Inter-VLAN Routing

### ⚙️ Implementation Strategy
1. **Define VLANs**: Segmented the network into HR (VLAN 10) and Finance (VLAN 20).
2. **Inter-VLAN Routing**: Configured Router-on-a-Stick to allow controlled communication.
3. **Security Hardening**: Implemented an Extended ACL on the router interface to restrict traffic between subnets.

### 🛡️ Security Hardening (ACL Configuration)
```bash
# Deny HR (192.168.10.0) access to Finance (192.168.20.0)
access-list 100 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255
# Permit all other traffic
access-list 100 permit ip any any
# Apply to HR gateway interface
interface GigabitEthernet0/0.10
 ip access-group 100 out
