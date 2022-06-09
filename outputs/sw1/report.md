# sw1 Commands Output

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
Vl10                           up             up                 
Vl20                           up             up
```
## show ip interface brief

```
Address
Interface         IP Address              Status       Protocol            MTU    Owner  
----------------- ----------------------- ------------ -------------- ----------- -------
Ethernet3         100.100.100.2/24        up           up                 1500           
Loopback0         1.1.1.1/32              up           up                65535           
Management1       192.168.22.191/24       up           up                 1500           
Vlan10            10.10.10.1/24           up           up                 1500           
Vlan20            20.20.20.1/24           up           up                 1500
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

 C        1.1.1.1/32 is directly connected, Loopback0
 C        10.10.10.0/24 is directly connected, Vlan10
 C        20.20.20.0/24 is directly connected, Vlan20
 O IA     30.30.30.0/24 [110/20] via 20.20.20.2, Vlan20
 O IA     40.40.40.0/24 [110/30] via 20.20.20.2, Vlan20
 O        50.50.50.0/24 [110/20] via 20.20.20.2, Vlan20
 O        60.60.60.0/24 [110/20] via 20.20.20.2, Vlan20
 C        100.100.100.0/24 is directly connected, Ethernet3
 C        192.168.22.0/24 is directly connected, Management1
```
## show lldp neighbors

```
Last table change time   : 1:25:42 ago
Number of table inserts  : 3
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
Et1           sw2                      Ethernet1           120
Et2           PCA                      Ethernet1           120
Et3           R1                       Ethernet1           120
```
## show running-config

```
! Command: show running-config
! device: sw1 (vEOS-lab, EOS-4.27.3F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
username ansible privilege 15 secret sha512 $6$qpS6W0UUvqX7xdUP$MCJZg6HPfiG0bPTsQvRWcDIwjQAHWbfhHOkbfgcgpI2TEZML18U9/u7EbZG93X/EgRO5EHySyDdeGav2zYJfF.
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
hostname sw1
!
spanning-tree mode mstp
!
vlan 10,20
!
interface Ethernet1
   switchport access vlan 20
!
interface Ethernet2
   switchport access vlan 10
!
interface Ethernet3
   no switchport
   ip address 100.100.100.2/24
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
   ip address 1.1.1.1/32
!
interface Management1
   ip address 192.168.22.191/24
!
interface Vlan10
   ip address 10.10.10.1/24
!
interface Vlan20
   ip address 20.20.20.1/24
!
ip routing
!
ip route 0.0.0.0/0 192.168.22.1
!
router ospf 1
   network 10.10.10.1/32 area 0.0.0.0
   network 20.20.20.1/32 area 0.0.0.0
   max-lsa 12000
   default-information originate always
!
end
```
## show version

```
Arista vEOS-lab
Hardware version: 
Serial number: 4E8486BB75039E4A0A43FC8F4497BA8A
Hardware MAC address: 5005.5161.f4e9
System MAC address: 5005.5161.f4e9

Software image version: 4.27.3F
Architecture: i686
Internal build version: 4.27.3F-26379303.4273F
Internal build ID: 13f8bd28-52d0-40ec-ab80-b12a056d63d4
Image format version: 1.0
Image optimization: None

Uptime: 17 hours and 22 minutes
Total memory: 4000404 kB
Free memory: 3085456 kB
```
