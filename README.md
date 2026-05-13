# IPSec-VPN-PT-Lab
Small enterprise network stimulation created with Packet Tracer. Demonstrates VLAN-based network segmentation as well as IPSec site-to-site VPN connectivity for secure communication over untrusted networks.

Topology:
![Network Topology](images/01-topology.png)

Technologies Implemented:
- Cisco Packet Tracer
- Cisco IOS CLI
- VLANs
- 802.1Q Trunking
- Router-on-a-Stick
- Static Routing
- Access Control Lists (ACLs)
- IPsec VPN
- ISAKMP/IKE

VLAN Config:
- Vlans assigned:
  - VLAN 10 – Management
  - VLAN 20 – HR
  - VLAN 30 – IT
  - VLAN 40 – Sales
- Assigned switch access ports to appropriate VLANs
- Configured trunk link between switch and router
- Implemented router-on-a-stick using router subinterfaces
- Assigned IP addresses, subnet masks, and default gateways to end devices
- Verified inter-VLAN communication

IPSec VPN Config:
- Configured ISAKMP policies for secure key exchange
- Defined IPsec transform sets for encryption and authentication
- Established a site-to-site VPN tunnel between two routers
- Verified encrypted traffic between remote networks



