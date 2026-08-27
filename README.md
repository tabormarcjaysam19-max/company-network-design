# Company Office Network Design
A Cisco Packet Tracer project that simulates a company office network using routers, Layer 2/Layer 3 switches, servers, printers, wireless access points, and an ASA firewall

## Network Topology
![Network Topology](screenshots/network-topology.png)

## Features Implemented
- VLAN segmentation
- Access and trunk port configuration
- Inter-VLAN routing
- IPv4 addressing
- DHCP and DNS services
- DHCP relay
- Static routing
- Corporate and guest Wi-Fi segmentation
- NAT/PAT
- ACL-based access control
- ASA firewall integration and security policies
- Management VLAN
- SSH remote management

## Devices Used
- 2 Cisco 2911 Routers
- 1 Cisco ASA 5506 Firewall
- 1 Cisco 3560 Layer 3 Core Switch
- 4 Cisco 2960 Access Switches
- 2 Wireless Access Points
- 3 Servers
- 2 Network Printers
- Employee PCs and laptops
  
## VLAN Design
| VLAN |     Name       |     Network     |
|------|----------------|-----------------|
|  10  |    Employees   | 192.168.10.0/24 |
|  20  |    Servers     | 192.168.20.0/24 |
|  30  |    Printers    | 192.168.30.0/24 |
|  40  |    Guest       | 192.168.40.0/24 |
|  50  |    Management  | 192.168.50.0/24 |

## IP Addressing Plan
| Device / Network | IP Address / Subnet |
|---|---|
| VLAN 10 - Employees | 192.168.10.0/24 |
| VLAN 20 - Servers | 192.168.20.0/24 |
| VLAN 30 - Printers | 192.168.30.0/24 |
| VLAN 40 - Guest Wi-Fi | 192.168.40.0/24 |
| VLAN 50 - Management | 192.168.50.0/24 |
| SW-CORE VLAN 10 Gateway | 192.168.10.1 |
| SW-CORE VLAN 20 Gateway | 192.168.20.1 |
| SW-CORE VLAN 30 Gateway | 192.168.30.1 |
| FIREWALL Guest Gateway | 192.168.40.1 |
| SW-CORE VLAN 50 Gateway | 192.168.50.1 |
| DNS/DHCP Server | 192.168.20.10 |
| File Server | 192.168.20.20 |
| Application Server | 192.168.20.30 |
| Printer 1 | 192.168.30.10 |
| Printer 2 | 192.168.30.11 |
| PC-IT | 192.168.50.100 |
| SW-ACCESS1 | 192.168.50.11 |
| SW-ACCESS2 | 192.168.50.12 |
| SW-ACCESS3 | 192.168.50.13 |
| SW-ACCESS4 | 192.168.50.14 |

## Network Access Policy
| Source Network | Destination | Access |
|---|---|---|
| Employees | Servers | Allowed |
| Employees | Printers | Allowed |
| Employees | Internet | Allowed |
| Guest Wi-Fi | Employees | Blocked |
| Guest Wi-Fi | Servers | Blocked |
| Guest Wi-Fi | Printers | Blocked |
| Guest Wi-Fi | Management | Blocked |
| Guest Wi-Fi | Internet | Allowed |
| Management | Network Devices | Allowed via SSH |
| Printers | Internet | Blocked |

Guest Wi-Fi is separated from the internal company network through the ASA firewall, while the management network is used for secure administration of switches through SSH.

## Security
The network separates employee, server, printer, guest, and management traffic using VLANs and ACLs. Guest Wi-Fi is isolated from internal company resources while retaining Internet access, and SSH is used for secure remote management of network devices.

## Testing and Verification

### VLAN Configuration
Verified VLANs for employees, servers, printers, guests, and network management.
![VLAN Configuration](screenshots/vlan-configuration.png)

### NAT/PAT
Verified NAT/PAT translation from private company IP addresses to the edge router's outside IP address.
![NAT/PAT Translation](screenshots/nat-pat-translation.png)

### Guest Network Security
Verified that guest Wi-Fi can access the simulated Internet while access to servers, printers, and management devices is blocked.
![Guest Network Security](screenshots/guest-acl-testing.png)

### SSH Remote Management
Verified secure remote management of network switches from the IT workstation using SSH.
![SSH Management](screenshots/ssh-management.png)

### Firewall Security Policy
Configured firewall rules to control traffic between the company network, guest network, and simulated Internet.
![Firewall Security Policy](screenshots/firewall-security-policy.png)

## Lab Testing
Network was tested to verify connectivity, segmentation, security, and remote management.

- Verified employee devices could reach their default gateway, servers, printers, and simulated Internet.
- Verified corporate Wi-Fi devices received the correct network access.
- Verified guest Wi-Fi could access the simulated Internet while internal company resources remained blocked.
- Verified VLAN communication through inter-VLAN routing.
- Verified NAT/PAT translations on the edge router.
- Verified SSH remote management from the IT workstation to network switches.
- Verified firewall rules and ACLs were enforcing the intended access policies.

## Skills Demonstrated
- Network design and IP addressing
- VLAN configuration and trunking
- Inter-VLAN routing
- DHCP and DNS configuration
- Static routing and NAT/PAT
- Wireless network segmentation
- ACL and firewall configuration
- Guest network isolation
- SSH remote management
- Network connectivity testing and troubleshooting
