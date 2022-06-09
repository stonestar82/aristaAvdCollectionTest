# sw3 Commands Output

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
Vl30                           up             up                 
Vl40                           up             up
```
## show ip interface brief

```
Address
Interface         IP Address              Status       Protocol            MTU    Owner  
----------------- ----------------------- ------------ -------------- ----------- -------
Loopback0         3.3.3.3/32              up           up                65535           
Management1       192.168.22.193/24       up           up                 1500           
Vlan30            30.30.30.2/24           up           up                 1500           
Vlan40            40.40.40.1/24           up           up                 1500
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

 C        3.3.3.3/32 is directly connected, Loopback0
 O IA     10.10.10.0/24 [110/30] via 30.30.30.1, Vlan30
 O IA     20.20.20.0/24 [110/20] via 30.30.30.1, Vlan30
 C        30.30.30.0/24 is directly connected, Vlan30
 C        40.40.40.0/24 is directly connected, Vlan40
 O IA     50.50.50.0/24 [110/20] via 30.30.30.1, Vlan30
 O IA     60.60.60.0/24 [110/20] via 30.30.30.1, Vlan30
 C        192.168.22.0/24 is directly connected, Management1
```
## show lldp neighbors

```
Last table change time   : 1:25:42 ago
Number of table inserts  : 2
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           sw2                      Ethernet2           120
Et2           PCB                      Ethernet1           120
```
## show running-config

```
! Command: show running-config
! device: sw3 (vEOS-lab, EOS-4.27.3F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
username ansible privilege 15 secret sha512 $6$LHGOTMXlbeOSyW/F$CTyH3/BSv013PRiTwd011GKesDIzqIEgdxU6r49STCLHS25SefcLp.7zIWXNfC/pvJxel3sDHEYW.0sjp5I8i1
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
hostname sw3
!
spanning-tree mode mstp
!
vlan 30,40
!
interface Ethernet1
   switchport access vlan 30
!
interface Ethernet2
   switchport access vlan 40
!
interface Ethernet3
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
   ip address 3.3.3.3/32
!
interface Management1
   ip address 192.168.22.193/24
!
interface Vlan30
   ip address 30.30.30.2/24
!
interface Vlan40
   ip address 40.40.40.1/24
!
ip routing
!
ip route 0.0.0.0/0 192.168.22.1
!
router ospf 1
   network 30.30.30.2/32 area 0.0.0.10
   network 40.40.40.1/32 area 0.0.0.10
   max-lsa 12000
!
end
```
## show version

```
Arista vEOS-lab
Hardware version: 
Serial number: D21AAF821E881EF2C8D914B3693F60F1
Hardware MAC address: 5052.66f3.9a5e
System MAC address: 5052.66f3.9a5e

Software image version: 4.27.3F
Architecture: i686
Internal build version: 4.27.3F-26379303.4273F
Internal build ID: 13f8bd28-52d0-40ec-ab80-b12a056d63d4
Image format version: 1.0
Image optimization: None

Uptime: 17 hours and 22 minutes
Total memory: 4000404 kB
Free memory: 3085608 kB
```
