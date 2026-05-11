🌐 **Enterprise Campus Network Topology (Cisco Packet Tracer)**

📌 **Project Overview**

This project is a fully designed enterprise-grade campus network topology built using Cisco Packet Tracer. It demonstrates core networking concepts such as VLAN segmentation, inter-VLAN routing, HSRP redundancy, and dynamic routing using OSPF.

The design focuses on high availability, fault tolerance, scalability, and redundancy, simulating a real-world enterprise environment.

🧱 Network Architecture

The network is designed using a three-router core layer with multiple VLAN-enabled access networks.

🔹 Core Devices
Router 1 (Core-R1)
Router 2 (Dist-R2)
Router 3 (Dist-R3)
Layer 2 Access Switches
🏢 VLAN Design
Department	VLAN ID	Network Address
MGMT	VLAN 10	192.168.10.0/24
ENGG	VLAN 20	192.168.20.0/24
HR	VLAN 30	192.168.30.0/24
SALES	VLAN 40	192.168.40.0/24
ACCOUNTING	VLAN 50	192.168.50.0/24
FINANCE	VLAN 60	192.168.60.0/24
🔁 IP Addressing (Router Links)
Connection	Network
R1 ↔ R2	10.10.10.0/24
R2 ↔ R3	10.10.30.0/24
R1 ↔ R3	10.10.20.0/24
⚙️ Key Technologies Implemented
VLAN Segmentation
802.1Q Trunking
Router-on-a-Stick Inter-VLAN Routing
OSPF Dynamic Routing (Area 0)
HSRP (Hot Standby Router Protocol)
Redundant Gateway Design
Link Failure Simulation & Recovery
🔁 HSRP Configuration Summary

HSRP is configured to provide default gateway redundancy across VLANs.

Virtual Gateway IP:
192.168.10.254
192.168.20.254
192.168.30.254
192.168.40.254
192.168.50.254
192.168.60.254
Load Balancing Strategy:

Active gateways are distributed between Dist-R2 and Dist-R3.

📡 OSPF Routing
Protocol: OSPF
Process ID: 1
Area: 0
Features:
Dynamic route advertisement
Automatic route recalculation
Fast convergence after link failure
Multiple path redundancy
🔧 Key Configurations
Router-on-a-Stick Example
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 standby 10 ip 192.168.10.254
OSPF Configuration
router ospf 1
 network 10.10.10.0 0.0.0.255 area 0
 network 10.10.20.0 0.0.0.255 area 0
 network 10.10.30.0 0.0.0.255 area 0
🔍 Verification Commands
VLANs
show vlan brief
Trunk Links
show interfaces trunk
Routing Table
show ip route
OSPF Neighbors
show ip ospf neighbor
HSRP Status
show standby brief
🔁 Failover Testing Results
✔ HSRP Gateway Failover
Active router automatically changes on failure
Virtual IP remains unchanged
No manual intervention required
✔ OSPF Reconvergence
Link failure triggers route recalculation
Alternate paths automatically used
Network remains fully operational
📸 Screenshots (Proof of Implementation)

Add your Packet Tracer screenshots here

Network Topology Overview
VLAN Configuration
Trunk Links Verification
Router Subinterfaces (Router-on-a-Stick)
HSRP Status Output
OSPF Neighbor Table
Routing Table (show ip route)
Failover Test (before/after shutdown)
🧠 Skills Demonstrated
Enterprise Network Design
Cisco IOS Configuration
VLAN & Trunking Implementation
Inter-VLAN Routing
Dynamic Routing (OSPF)
High Availability Design (HSRP)
Network Troubleshooting
Failover Simulation
🚀 Key Highlights

✔ Fully redundant network design
✔ High availability using HSRP
✔ Dynamic routing with OSPF
✔ Real-world enterprise architecture
✔ Load-balanced gateway design
✔ Automatic failover and recovery

📈 Future Improvements
DHCP Server Integration
ACL Security Policies
Port Security on Switches
EtherChannel Implementation
SSH Remote Management
Syslog Monitoring Server
NAT/PAT Internet Simulation
👨‍💻 Author

Created for enterprise networking practice using Cisco Packet Tracer.

🏁 Conclusion

This project demonstrates a production-style enterprise campus network with redundancy, dynamic routing, and scalable VLAN architecture. It simulates real-world networking behavior used in modern organizations.
