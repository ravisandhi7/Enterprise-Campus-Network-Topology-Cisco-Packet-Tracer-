🌐 **Enterprise Campus Network Topology (Cisco Packet Tracer)**

📌 **Project Overview**

This project is a fully designed enterprise-grade campus network topology built using Cisco Packet Tracer. It demonstrates core networking concepts such as VLAN segmentation, inter-VLAN routing, HSRP redundancy, and dynamic routing using OSPF.

The design focuses on high availability, fault tolerance, scalability, and redundancy, simulating a real-world enterprise environment.

🧱 **Network Architecture**

The network is designed using a three-router core layer with multiple VLAN-enabled access networks.

![TOPOLOGY](screenshots/topology/TOPOLOGY.png)

🔹 **Core Devices**

**Routers:**

Core-R1

Dist-R2

Dist-R3

**Layer 2 Switches:**

SW-Core-1

SW-Core-2

SW-MGMT

SW-ENGG

SW-HR

SW-SALES

SW-ACCOUNTING

SW-FINANCE

🏢 **VLAN Design**

Department	VLAN ID	Network Address

MGMT	VLAN 10	192.168.10.0/24

ENGG	VLAN 20	192.168.20.0/24

HR	VLAN 30	192.168.30.0/24

SALES	VLAN 40	192.168.40.0/24

ACCOUNTING	VLAN 50	192.168.50.0/24

FINANCE	VLAN 60	192.168.60.0/24

![VLANS_SW_CORE_1](screenshots/vlan/VLANS_SW_CORE_1.png)

![VLANS_SW_CORE_2](screenshots/vlan/VLANS_SW_CORE_2.png)

![VLAN10_SW_MGMT](screenshots/vlan/VLAN10_SW_MGMT.png)

![VLAN20_SW_ENGG](screenshots/vlan/VLAN20_SW_ENGG.png)

![VLAN30_SW_HR](screenshots/vlan/VLAN30_SW_HR.png)

![VLAN40_SW_SALES](screenshots/vlan/VLAN40_SW_SALES.png)

![VLAN50_SW_ACCOUNTING](screenshots/vlan/VLAN50_SW_ACCOUNTING.png)

![VLAN60_SW_FINANCE](screenshots/vlan/VLAN60_SW_FINANCE.png)


🔁 **IP Addressing (Router Links)**

Connection	Network

R1 ↔ R2	10.10.10.0/24

R2 ↔ R3	10.10.30.0/24

R1 ↔ R3	10.10.20.0/24

⚙️ **Key Technologies Implemented**

VLAN Segmentation

802.1Q Trunking

Router-on-a-Stick Inter-VLAN Routing

OSPF Dynamic Routing (Area 0)

HSRP (Hot Standby Router Protocol)

Redundant Gateway Design

Link Failure Simulation & Recovery

🔁 **HSRP Configuration Summary**

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

![HSRP](screenshots/hsrp/STANDBY_BRIEF_DIST_R2.png)

![HSRP](screenshots/hsrp/STANDBY_BRIEF_DIST_R3.png)

📡 **OSPF Routing**

Protocol: OSPF

Process ID: 1

Area: 0

**Features:**

Dynamic route advertisement

Automatic route recalculation

Fast convergence after link failure

Multiple path redundancy

🔧 **Key Configurations**

**Router-on-a-Stick Example**

interface GigabitEthernet0/0.10

 encapsulation dot1Q 10
 
 ip address 192.168.10.1 255.255.255.0
 
 standby 10 ip 192.168.10.254

  ![INTERFACE_TRUNK_SW_CORE_1](screenshots/trunking/INTERFACE_TRUNK_SW_CORE_1.png)

  ![ROAS_DIST_R2](screenshots/trunking/ROAS_DIST_R2.png)

  ![INTERFACE_TRUNK_SW_CORE_2](screenshots/trunking/INTERFACE_TRUNK_SW_CORE_2.png)

  ![ROAS_DIST_R3](screenshots/trunking/ROAS_DIST_R3.png)


**OSPF Configuration**

router ospf 1

 network 10.10.10.0 0.0.0.255 area 0
 
 network 10.10.20.0 0.0.0.255 area 0
 
 network 10.10.30.0 0.0.0.255 area 0

 ![RUNNING_CONFIG_DIST_R2_OSPF](screenshots/ospf/RUNNING_CONFIG_DIST_R2_OSPF.png)

 ![RUNNING_CONFIG_DIST_R3_OSPF](screenshots/ospf/RUNNING_CONFIG_DIST_R3_OSPF.png)


**🔍 Verification Commands**

VLANs - show vlan brief

Trunk Links - show interfaces trunk

Routing Table - show ip route

OSPF Neighbors - show ip ospf neighbor

HSRP Status - show standby brief

🔁 **Failover Testing Results**

✔ **OSPF Reconvergence and Link Failure Simulation**

Active router automatically changes on failure

Virtual IP remains unchanged

No manual intervention required

 ![OSPF_Reconvergence_and_Link_Failure_Simulation](screenshots/ospf/OSPF_Reconvergence_and_Link_Failure_Simulation.png)

 A failover test was performed by shutting down the VLAN interface on Dist-R2. OSPF adjacency reconverged automatically, demonstrating network resiliency and dynamic routing recovery.


✔ **OSPF Link Recovery and Reconvergence**

Link failure triggers route recalculation

Alternate paths automatically used

Network remains fully operational

 ![OSPF_Link_Recovery_and_Reconvergence](screenshots/ospf/OSPF_Link_Recovery_and_Reconvergence.png)

The OSPF network dynamically adapted to a simulated link failure on GigabitEthernet0/1. After the interface was restored, OSPF automatically reconverged and reinstated all routing paths without manual intervention, demonstrating high availability and network resilience.

✔ **HSRP Active/Standby Gateway Redundancy**

 ![HSRP_FAILOVER_DIST_R2](screenshots/hsrp/HSRP_FAILOVER_DIST_R2.png)

  ![HSRP_FAILOVER_DIST_R3](screenshots/hsrp/HSRP_FAILOVER_DIST_R3.png)


HSRP maintained gateway availability using virtual IP addresses. Active and standby roles were distributed across routers to ensure continuous network access during failures.

🧠 **Skills Demonstrated**

Enterprise Network Design

Cisco IOS Configuration

VLAN & Trunking Implementation

Inter-VLAN Routing

Dynamic Routing (OSPF)

High Availability Design (HSRP)

Network Troubleshooting

Failover Simulation

🚀 **Key Highlights**

✔ Fully redundant network design

✔ High availability using HSRP

✔ Dynamic routing with OSPF

✔ Real-world enterprise architecture

✔ Load-balanced gateway design

✔ Automatic failover and recovery

📈 **Future Improvements**

DHCP Server Integration

ACL Security Policies

Port Security on Switches

EtherChannel Implementation

SSH Remote Management

Syslog Monitoring Server

NAT/PAT Internet Simulation

👨‍💻 **Author**

Ravi Kumar

🏁 **Conclusion**

This project demonstrates a production-style enterprise campus network with redundancy, dynamic routing, and scalable VLAN architecture. It simulates real-world networking behavior used in modern organizations.
