🗺️ Network Topology and IP Addressing Scheme
🧭 Overview
The network topology consists of a centralized Head Office and seven Provincial Branches, each connected through a Network Service Provider (NSP). The design emphasizes scalability, performance, and redundancy, particularly at the core (Head Office). Each site has been carefully subnetted according to user count and future growth projections.

🏢 Head Office: Centralized Core Network
Total Employees: 480

Subnet: 192.168.0.0/22 (1024 IPs)

Subnet Mask: 255.255.252.0

IP Range: 192.168.0.1 - 192.168.3.254

Usable IPs: 1022

Reserved IPs: 192.168.0.1-10, 192.168.3.205-254

DHCP Pool: 192.168.0.11 - 192.168.3.204

The Head Office is further segmented into four VLANs, each representing a department:

VLAN	Department	Subnet	Purpose
10	Admin	192.168.2.0/25	User devices
20	Finance	192.168.0.0/23	Financial systems
30	Loan	192.168.3.0/24	Loan processing
40	IT	192.168.2.128/25	IT infrastructure

Routing: Inter-VLAN routing is implemented via Router-on-a-Stick. DHCP services and default gateways for each VLAN are managed by the Head Office router.

Redundancy: The Head Office is connected to the NSP via two WAN links (primary and backup) for high availability.

🏬 Branch Offices: Distributed Subnets
Each branch has its own subnet, sized according to the number of users. All branch offices connect to the NSP cloud through point-to-point /30 links.

Branch	Employees	Subnet Size	Subnet	Mask	IP Range	Usable IPs	Reserved IPs	DHCP Pool
Province 1	70	/24	192.168.10.0/24	255.255.255.0	192.168.10.1 - 192.168.10.254	254	192.168.10.1-10, 192.168.10.205-254	192.168.10.11 - 192.168.10.204
Province 2	95	/24	192.168.11.0/24	255.255.255.0	192.168.11.1 - 192.168.11.254	254	192.168.11.1-10, 192.168.11.205-254	192.168.11.11 - 192.168.11.204
Province 3	300	/23	192.168.4.0/23	255.255.254.0	192.168.4.1 - 192.168.5.254	510	192.168.4.1-10, 192.168.5.205-254	192.168.4.11 - 192.168.5.204
Province 4	175	/24	192.168.12.0/24	255.255.255.0	192.168.12.1 - 192.168.12.254	254	192.168.12.1-10, 192.168.12.205-254	192.168.12.11 - 192.168.12.204
Province 5	450	/23	192.168.6.0/23	255.255.254.0	192.168.6.1 - 192.168.7.254	510	192.168.6.1-10, 192.168.7.205-254	192.168.6.11 - 192.168.7.204
Province 6	280	/23	192.168.8.0/23	255.255.254.0	192.168.8.1 - 192.168.9.254	510	192.168.8.1-10, 192.168.9.205-254	192.168.8.11 - 192.168.9.204
Province 7	120	/24	192.168.13.0/24	255.255.255.0	192.168.13.1 - 192.168.13.254	254	192.168.13.1-10, 192.168.13.205-254	192.168.13.11 - 192.168.13.204

Routing: Branch routers use either static routing or RIP to communicate with the Head Office and other branches through the NSP.

DHCP Configuration: Each branch router provides DHCP to local hosts, excluding reserved IPs.
