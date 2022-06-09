# sw2 Commands Output

## Table of Contents

- [show lldp neighbors](#show-lldp-neighbors)
- [show ip interface brief](#show-ip-interface-brief)
- [show interfaces description](#show-interfaces-description)
- [show ip route](#show-ip-route)
- [show version](#show-version)
- [show running-config](#show-running-config)
## show interfaces description

```
Interface                      Status         Protocol           Description
Et1                            up             up                 
Et2                            up             up                 
Et3                            up             up                 
Et4                            up             up                 
Et5                            up             up                 
Et6                            up             up                 
Et7                            up             up                 
Et8                            up             up                 
Lo0                            up             up                 
Ma1                            up             up                 
Vl20                           up             up                 
Vl30                           up             up                 
Vl50                           up             up                 
Vl60                           up             up
```
## show ip interface brief

```
Address
Interface         IP Address              Status       Protocol            MTU    Owner  
----------------- ----------------------- ------------ -------------- ----------- -------
Loopback0         2.2.2.2/32              up           up                65535           
Management1       192.168.22.192/24       up           up                 1500           
Vlan20            20.20.20.2/24           up           up                 1500           
Vlan30            30.30.30.1/24           up           up                 1500           
Vlan50            50.50.50.1/24           up           up                 1500           
Vlan60            60.60.60.1/24           up           up                 1500
```
## show ip route

```
VRF: default
Codes: C - connected, S - static, K - kernel, 
       O - OSPF, IA - OSPF inter area, E1 - OSPF external type 1,
       E2 - OSPF external type 2, N1 - OSPF NSSA external type 1,
       N2 - OSPF NSSA external type2, B - Other BGP Routes,
       B I - iBGP, B E - eBGP, R - RIP, I L1 - IS-IS level 1,
       I L2 - IS-IS level 2, O3 - OSPFv3, A B - BGP Aggregate,
       A O - OSPF Summary, NG - Nexthop Group Static Route,
       V - VXLAN Control Service, M - Martian,
       DH - DHCP client installed default route,
       DP - Dynamic Policy Route, L - VRF Leaked,
       G  - gRIBI, RC - Route Cache Route

Gateway of last resort:
 S        0.0.0.0/0 [1/0] via 192.168.22.1, Management1

 C        2.2.2.2/32 is directly connected, Loopback0
 O        10.10.10.0/24 [110/20] via 20.20.20.1, Vlan20
 C        20.20.20.0/24 is directly connected, Vlan20
 C        30.30.30.0/24 is directly connected, Vlan30
 O        40.40.40.0/24 [110/20] via 30.30.30.2, Vlan30
 C        50.50.50.0/24 is directly connected, Vlan50
 C        60.60.60.0/24 is directly connected, Vlan60
 C        192.168.22.0/24 is directly connected, Management1
```
## show lldp neighbors

```
Last table change time   : 1:25:43 ago
Number of table inserts  : 3
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           sw1                      Ethernet1           120
Et2           sw3                      Ethernet1           120
Et3           L2_SW                    Ethernet1           120
```
## show running-config

```
! Command: show running-config
! device: sw2 (vEOS-lab, EOS-4.27.3F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
username ansible privilege 15 secret sha512 $6$TN0hdt2vPgy/XOdu$ICBH1psVBpBRNfamtV6pfM6XM56dQU9e20qtFSit4KK8NuU8ODCFTBSYGklN4HYwizJ5vTuS5KLlevnZuxcLk1
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
logging buffered 1000
logging console informational
logging monitor informational
logging synchronous level all
!
hostname sw2
!
spanning-tree mode mstp
!
vlan 20,30,50,60
!
interface Ethernet1
   switchport access vlan 20
!
interface Ethernet2
   switchport access vlan 30
!
interface Ethernet3
   switchport trunk allowed vlan 50,60
   switchport mode trunk
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Loopback0
   ip address 2.2.2.2/32
!
interface Management1
   ip address 192.168.22.192/24
!
interface Vlan20
   ip address 20.20.20.2/24
!
interface Vlan30
   ip address 30.30.30.1/24
!
interface Vlan50
   ip address 50.50.50.1/24
!
interface Vlan60
   ip address 60.60.60.1/24
!
ip routing
!
ip route 0.0.0.0/0 192.168.22.1
!
router ospf 1
   network 20.20.20.2/32 area 0.0.0.0
   network 30.30.30.1/32 area 0.0.0.10
   network 50.50.50.1/32 area 0.0.0.0
   network 60.60.60.1/32 area 0.0.0.0
   max-lsa 12000
!
end
```
## show version

```
Arista vEOS-lab
Hardware version: 
Serial number: 1FB0E44F719E9FB6600CCB9D61D7E2C3
Hardware MAC address: 5088.97c1.28a9
System MAC address: 5088.97c1.28a9

Software image version: 4.27.3F
Architecture: i686
Internal build version: 4.27.3F-26379303.4273F
Internal build ID: 13f8bd28-52d0-40ec-ab80-b12a056d63d4
Image format version: 1.0
Image optimization: None

Uptime: 17 hours and 22 minutes
Total memory: 4000404 kB
Free memory: 3085544 kB
```
