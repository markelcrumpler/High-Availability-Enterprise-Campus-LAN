High Availability Enterprise Campus LAN
Markel Crumpler

Topology 
Objective
Design a highly available campus network utilizing Layer 2 and Layer 3 redundancy to eliminate single points of failure at the core and distribution layers.



Technologies Deployed

•	VLANs and 802.1Q Trunking.
•	Layer 2 EtherChannel utilizing LACP.
•	Rapid PVST+ Spanning Tree Protocol.
•	First Hop Redundancy Protocols (FHRP) using HSRP.
•	Single-Area OSPFv2 for internal routing.
•	Centralized DHCP with IP Helper Addresses.
Configuration Insight

•	To prevent network loops while maximizing bandwidth, I configured LACP between the Core and Access switches.

•	HSRP on CORE-1 and CORE-2 to provide a virtual default gateway for VLANs 10 and 20.

•	Established a virtual IP as the default gateway so that if Core-1 suffers a hardware failure, Core-2 will immediately resume routing duties without dropping client connections.
Security and Access

•	Mitigated VLAN hopping attacks by explicitly disabling Dynamic Trunking Protocol (DTP) using the switchport nonegotiate command and hardcoding all 802.1Q trunks

•	Isolated network infrastructure traffic to a dedicated Management/Native network (VLAN 99) and enforced SSH-only remote access on VTY lines to prevent cleartext credential interception

•	Secured the enterprise boundary by designing and deploying Extended Access Control Lists (ACLs) to filter TCP/IP packets

o	Enforced strict corporate access policies by explicitly permitting the Marketing department (VLAN 10) to reach external internet targets while actively denying internet access to restricted subnets like Engineering (VLAN 20)
