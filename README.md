# OSPF-LAB-02

Welcome to OSPF lesson 102
Be able to explain:
1. Explain the purpose of a hierarchical routing design and why flat OSPF fails at scale.
Flat, or single area OSPF, fails at scale because of memory limitations. To reduce how much each router has to remember, multi-area OSPF subdivides a massive network to allow routers to effectivly sumarize routes.  
2. Design and configure a multi-area topology featuring a central backbone (Area 0).
all other areas  must connect to the backbone, area 0. All areas must be continuous. for example: there cannot be two unconnected sets of routers designated area 3.
3. Correctly identify and configure Area Border Routers (ABRs).
Area border routers have at least one interface in one area and a second interface in another. 
configuration:
   R3#(config) int G0/0/0
   R3#(config-if) ip ospf 1 area 0
   R3#(config) int G0/0/1
   R3#(config-if) ip ospf 1 area 2
   
5. Verify routing tables, LSDB (Link State Database), and neighbor adjacencies using CLI commands.
   R>show route ! This displays routes currently in use. 
   R>show ip ospf neighbor ! Displays neighbors
   R>show ip ospf border-routers ! Displays border routers and boundry information.
   R>show ip ospf database ! Displays information about ospf.
   
Things to remember:
The Contiguous Area 0 Rule: connecting two non-backbone areas directly without passing traffic through Area 0, will violate core OSPF architecture rules.

Network Statement Typos: A misplaced wildcard mask or wrong area ID will silently fail to form adjacencies without throwing obvious syntax errors.

DR/BDR Confusion: In broadcast multi-access networks (like Ethernet segments), Designated Routers and Backup Designated Routers dictate how adjacencies form, which can alter expected neighbor states.


Goal:


As muscle-memory practice. Set up hostnames for some of the routers. 
Router 4 as R4
Router 5 as R5
Router 6 as R6

Set up Router interfaces for some of the routers. 
Router 4 as 4.4.4.4
Router 5 as 5.5.5.5
Router 6 as 6.6.6.6

Activate OSPF per-interface and set area according to this scheme.
-  Designate interfaces facing R0 as area 0
-  Designate interfaces facing R1,R2,R3 to area 1
-  Designate interfaces facing R4,R5,R6 to area 2

More practice:
Configure R4's LAN-facing interface as passive.
Adjust OSPF interface cost to favor the path though R5.



Topology:
Device	| IP address		| Subnet		| Designated Gateway

ISP	| G0/0/0 = 10.1.1.1 	| 255.255.255.252; 

R0	| G0/0/0 = 10.1.1.2	| 255.255.255.252; 
R0	| G0/0/1 = 10.1.2.1 	| 255.255.255.252; 
R0	| G0/0/2 = 10.1.3.1 	| 255.255.255.252; 

R1 	| G0/0/0 = 10.1.4.1 	| 255.255.255.252; 
R1 	| G0/0/1 = 10.1.4.5 	| 255.255.255.252
R1 	| G0/0/2 = 192.168.1.1	| 255.255.255.0

R2 	| G0/0/0 = 10.1.4.2 	| 255.255.255.252; 
R2 	| G0/0/1 = 10.1.4.9  	| 255.255.255.252
R2 	| G0/0/2 = 192.168.2.1 	| 255.255.255.0

R3 	| G0/0/0 = 10.1.4.6 	| 255.255.255.252; 
R3 	| G0/0/1 = 10.1.4.10	| 255.255.255.252; 
R3 	| G0/0/2 = 10.1.2.2 	| 255.255.255.252; 

R4 	| G0/0/0 = 10.1.5.1 	| 255.255.255.252
R4 	| G0/0/1 = 10.1.5.5 	| 255.255.255.252
R4 	| G0/0/2 = 192.168.3.1	| 255.255.255.0

R5 	| G0/0/0 = 10.1.5.2 	| 255.255.255.252; 
R5 	| G0/0/1 = 10.1.5.9  	| 255.255.255.252
R5 	| G0/0/2 = None	 	| None

R6 	| G0/0/0 = 10.1.5.10 	| 255.255.255.252; 
R6 	| G0/0/1 = 10.1.5.6 	| 255.255.255.252; 
R6 	| G0/0/2 = 10.1.3.2 	| 255.255.255.252; 


PC1 	| F0/0 192.168.1.10 	| 255.255.255.0; 	| DG = Not Set
PC2 	| F0/0 192.168.2.10	| 255.255.255.0; 	| DG = Not Set
PC3 	| F0/0 192.168.3.10	| 255.255.255.0; 	| DG = Not Set
 
