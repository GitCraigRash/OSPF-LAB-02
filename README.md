# OSPF-LAB-02

Welcome to OSPF lesson 102
Goal:
-  Activate OSPF globally on all routers
-  Designate R0 as Area0
-  Designate R1,R2,R3 to area 1
-  Designate R4,R5,R6 to area 2
-  Activate OSPF per-interface  and set area according to this scheme.
-  
- Configure all Routers to be OSPF neighbors and advertising their routes.
- 
- Configure LAN-facing  interfaces passive. 
- Adjust OSPF interface cost to favor the path though R1.


- Experiment: Change the hello timer on one router and observe where adjacency breaks.

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

R6 	| G0/0/0 = 10.1.5.6 	| 255.255.255.252; 
R6 	| G0/0/1 = 10.1.5.10 	| 255.255.255.252; 
R6 	| G0/0/2 = 10.1.3.2 	| 255.255.255.252; 


PC1 	| F0/0 192.168.1.10 	| 255.255.255.0; 	| DG = Not Set
PC2 	| F0/0 192.168.2.10	| 255.255.255.0; 	| DG = Not Set
PC3 	| F0/0 192.168.3.10	| 255.255.255.0; 	| DG = Not Set
 
