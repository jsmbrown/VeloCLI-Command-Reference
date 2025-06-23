#	--bgpd_dump

##	Description
This command displays the status of the Border Gateway Protocol (BGP) database on the VeloCloud Edge. It provides insights into the BGP daemon's current state, including information about BGP peers, learned routes, and other operational parameters. This is useful for troubleshooting BGP routing issues within the SD-WAN environment.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --bgpd_dump
```
*(The output of this command will be a dump of BGP daemon status information, which can be extensive and vary based on the BGP configuration and current state. It is not typically presented in a fixed tabular format.)*
```
example_com:velocli> debug --bgpd_dump
show running-config
===================
Building configuration...

Current configuration:
!
frr version 8.2
frr defaults traditional
hostname vc-edge
log file /var/log/bgpd.log
!
debug bgp neighbor-events
debug bgp updates in
debug bgp updates out
debug bgp zebra
debug bgp zebra evpn
!
password zebra
!
router bgp 65000 vrf [vc:1:1]
 bgp update-group-split-horizon
 neighbor 172.30.255.36 remote-as 65515
 neighbor 172.30.255.36 ebgp-multihop 2
 neighbor 172.30.255.37 remote-as 65515
 neighbor 172.30.255.37 ebgp-multihop 2
 !
 address-family ipv4 unicast
  redistribute connected
  redistribute static
  redistribute user
  neighbor 172.30.255.36 default-originate route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  neighbor 172.30.255.36 soft-reconfiguration inbound
  neighbor 172.30.255.36 route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 in
  neighbor 172.30.255.36 route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 out
  neighbor 172.30.255.37 default-originate route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  neighbor 172.30.255.37 soft-reconfiguration inbound
  neighbor 172.30.255.37 route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 in
  neighbor 172.30.255.37 route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 out
  maximum-paths 2
  maximum-paths ibgp 2
 exit-address-family
 !
 address-family ipv6 unicast
  redistribute connected
  redistribute static
  redistribute user
  maximum-paths 2
  maximum-paths ibgp 2
 exit-address-family
!
access-list vty seq 5 permit 127.0.0.0/8
access-list vty seq 10 deny any
!
ip prefix-list PL_seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985_1 seq 5 permit 0.0.0.0/0
ip prefix-list PL_seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985_2 seq 5 permit 0.0.0.0/0 le 32
!
route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 deny 1
 match ip address prefix-list PL_seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985_1
!
route-map seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985 permit 2
 match ip address prefix-list PL_seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985_2
!
line vty
 access-class vty
!
end

sh bgp vrf all summary
===================

Instance [vc:1:1]:

IPv4 Unicast Summary:

BGP view name [vc:1:1]
BGP router identifier 1.2.3.4, local AS number 65000 vrf-id 1
BGP table version 164
RIB entries 15, using 2880 bytes of memory
Peers 2, using 44 KiB of memory

Neighbor        V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd      PfxSnt
172.30.255.36   4      65515     22945     20264        0    0    0 01w6d22h            2           7
172.30.255.37   4      65515     14920     13183        0    0    0 01w2d01h            2           9

Total number of neighbors 2

sh bgp vrf all neighbors
===================

Instance [vc:1:1]:
BGP neighbor is 172.30.255.36, remote AS 65515, local AS 65000, external link
  BGP version 4, remote router ID 172.30.255.36, local router ID 1.2.3.4
  BGP state = Established, up for 01w6d22h
  Last read 00:00:11, Last write 00:00:38
  Hold time is 180 seconds, keepalive interval is 60 seconds
  Configured hold time is 180, keepalive interval is 60 seconds
  Configured hold time is 180 seconds, keepalive interval is 60 seconds
  Neighbor capabilities:
    4 Byte AS: advertised and received
    AddPath:
      IPv4 Unicast: RX advertised
    Route refresh: advertised and received(new)
    Address Family IPv4 Unicast: advertised and received
    Address Family IPv6 Unicast: received
    Hostname Capability: advertised (name: vc-edge,domain name: n/a) not received
    Graceful Restart Capability: advertised
  Graceful restart information:
    Local GR Mode: Helper*
    Remote GR Mode: Disable
    R bit: False
    Timers:
      Configured Restart Time(sec): 120
      Received Restart Time(sec): 0
  Message statistics:
    Inq depth is 0
    Outq depth is 0
                         Sent       Rcvd
    Opens:                  1          1
    Notifications:          0          0
    Updates:              176          1
    Keepalives:         20087      22943
    Route Refresh:          0          0
    Capability:             0          0
    Total:              20264      22945
  Minimum time between advertisement runs is 0 seconds

 For address family: IPv4 Unicast
  Update group 3, subgroup 1
  Packet Queue length 0
  Inbound soft reconfiguration allowed
  Community attribute sent to this neighbor(all)
  Default information originate, default route-map *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985, default not sent
  Inbound path policy configured
  Outbound path policy configured
  Route map for incoming advertisements is *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  Route map for outgoing advertisements is *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  2 accepted prefixes

  Connections established 1; dropped 0
  Last reset 01w6d22h, due to Waiting for peer OPEN
  External BGP neighbor may be up to 2 hops away.
Local host: 172.30.1.200, Local port: 179
Foreign host: 172.30.255.36, Foreign port: 63910
Nexthop: 172.30.1.200
Nexthop global: ::
Nexthop local: ::
BGP connection: shared network
BGP Connect Retry Timer in Seconds: 120
Read thread: on  Write thread: on  FD used: 21

BGP neighbor is 172.30.255.37, remote AS 65515, local AS 65000, external link
  BGP version 4, remote router ID 172.30.255.37, local router ID 1.2.3.4
  BGP state = Established, up for 01w2d01h
  Last read 00:00:43, Last write 00:00:24
  Hold time is 180 seconds, keepalive interval is 60 seconds
  Configured hold time is 180, keepalive interval is 60 seconds
  Configured hold time is 180 seconds, keepalive interval is 60 seconds
  Neighbor capabilities:
    4 Byte AS: advertised and received
    AddPath:
      IPv4 Unicast: RX advertised
    Route refresh: advertised and received(new)
    Address Family IPv4 Unicast: advertised and received
    Address Family IPv6 Unicast: received
    Hostname Capability: advertised (name: vc-edge,domain name: n/a) not received
    Graceful Restart Capability: advertised
  Graceful restart information:
    Local GR Mode: Helper*
    Remote GR Mode: Disable
    R bit: False
    Timers:
      Configured Restart Time(sec): 120
      Received Restart Time(sec): 0
  Message statistics:
    Inq depth is 0
    Outq depth is 0
                         Sent       Rcvd
    Opens:                  1          1
    Notifications:          0          0
    Updates:              144          1
    Keepalives:         13038      14918
    Route Refresh:          0          0
    Capability:             0          0
    Total:              13183      14920
  Minimum time between advertisement runs is 0 seconds

 For address family: IPv4 Unicast
  Update group 3, subgroup 1
  Packet Queue length 0
  Inbound soft reconfiguration allowed
  Community attribute sent to this neighbor(all)
  Default information originate, default route-map *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985, default not sent
  Inbound path policy configured
  Outbound path policy configured
  Route map for incoming advertisements is *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  Route map for outgoing advertisements is *seg1_6af9ce63c40b5c45ce6e810e2bcecd22831f67f1_1749485774985
  2 accepted prefixes

  Connections established 1; dropped 0
  Last reset 01w6d22h, due to Waiting for peer OPEN
  External BGP neighbor may be up to 2 hops away.
Local host: 172.30.1.200, Local port: 32867
Foreign host: 172.30.255.37, Foreign port: 179
Nexthop: 172.30.1.200
Nexthop global: ::
Nexthop local: ::
BGP connection: shared network
BGP Connect Retry Timer in Seconds: 120
Estimated round trip time: 4 ms
Read thread: on  Write thread: on  FD used: 24



show ip bgp vrf all
===================

Instance [vc:1:1]:
BGP table version is 164, local router ID is 1.2.3.4, vrf id 1
Default local pref 100, local AS 65000
Status codes:  s suppressed, d damped, h history, * valid, > best, = multipath,
               i internal, r RIB-failure, S Stale, R Removed
Nexthop codes: @NNN nexthop's vrf id, < announce-nh-self
Origin codes:  i - IGP, e - EGP, ? - incomplete

   Network          Next Hop            Metric LocPrf Weight Path
*> 1.2.3.4/32       0.0.0.0                  0         32768 ?
*> 10.10.10.1/32    0.0.0.0                 94         32768 ?
*> 172.22.0.0/16    0.0.0.0                  4         32768 64909 65515 ?
*> 172.22.1.4/32    0.0.0.0                  4         32768 64909 65515 ?
*= 172.30.0.0/16    172.30.255.37                          1 65515 i
*>                  172.30.255.36                          1 65515 i
*> 172.30.1.0/24    0.0.0.0                  0         32768 ?
*= 172.31.0.0/24    172.30.255.37                          1 65515 i
*>                  172.30.255.36                          1 65515 i
*> 172.31.1.0/24    0.0.0.0                  4         32768 64909 65515 ?
*> 192.168.105.0/24 0.0.0.0                  4         32768 64909 65515 ?

Displayed  9 routes and 11 total paths

show bgp vrf all ipv6
===================

Instance [vc:1:1]:
No BGP prefixes displayed, 0 exist

BGP View for segment ID: [vc:1:1]
===========================
BGP table version is 164, local router ID is 1.2.3.4, vrf id 1
Default local pref 100, local AS 65000
Status codes:  s suppressed, d damped, h history, * valid, > best, = multipath,
               i internal, r RIB-failure, S Stale, R Removed
Nexthop codes: @NNN nexthop's vrf id, < announce-nh-self
Origin codes:  i - IGP, e - EGP, ? - incomplete

   Network          Next Hop            Metric LocPrf Weight Path
*> 1.2.3.4/32       0.0.0.0                  0         32768 ?
*> 10.10.10.1/32    0.0.0.0                 94         32768 ?
*> 172.22.0.0/16    0.0.0.0                  4         32768 64909 65515 ?
*> 172.22.1.4/32    0.0.0.0                  4         32768 64909 65515 ?
*= 172.30.0.0/16    172.30.255.37                          1 65515 i
*>                  172.30.255.36                          1 65515 i
*> 172.30.1.0/24    0.0.0.0                  0         32768 ?
*= 172.31.0.0/24    172.30.255.37                          1 65515 i
*>                  172.30.255.36                          1 65515 i
*> 172.31.1.0/24    0.0.0.0                  4         32768 64909 65515 ?
*> 192.168.105.0/24 0.0.0.0                  4         32768 64909 65515 ?

Displayed  9 routes and 11 total paths

NS interface list for segment ID: [vc:1:1]
====================================
bgp1: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1320
        inet 172.30.1.200  netmask 255.255.255.0  destination 172.30.1.200
        inet6 fe80::1620:5f6b:e08c:5326  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 500  (UNSPEC)
        RX packets 314656  bytes 16436901 (15.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 96313  bytes 5626070 (5.3 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip6tnl0: flags=128<NOARP>  mtu 1452
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16  bytes 2112 (2.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 2112 (2.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tunl0: flags=128<NOARP>  mtu 1480
        tunnel   txqueuelen 1000  (IPIP Tunnel)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


NS route list for segment ID: [vc:1:1]
================================
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 bgp1
172.30.1.0      0.0.0.0         255.255.255.0   U     0      0        0 bgp1

NS IPv6 route list for segment ID: [vc:1:1]
================================
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
fe80::/64                      [::]                       U    256 1     0 bgp1
[::]/0                         [::]                       U    1024 1     0 bgp1
localhost/128                  [::]                       Un   0   3     0 lo
fe80::1620:5f6b:e08c:5326/128  [::]                       Un   0   2     0 bgp1
ff00::/8                       [::]                       U    256 2     0 bgp1
[::]/0                         [::]                       !n   -1  1     0 lo

NS netstat dump for segment ID: [vc:1:1]
==================================
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:179             0.0.0.0:*               LISTEN      15962/bgpd          
tcp        0      0 172.30.1.200:179        172.30.255.36:63910     ESTABLISHED 15962/bgpd          
tcp        0      0 172.30.1.200:32867      172.30.255.37:179       ESTABLISHED 15962/bgpd          
tcp6       0      0 :::179                  :::*                    LISTEN      15962/bgpd          


```
 


##  Field descriptions
The output of `debug --bgpd_dump` is a direct dump of the BGP daemon's internal status and database. It does not have a fixed columnar output. The information displayed will include details such as:
*   BGP router ID
*   Configured BGP neighbors (peers) and their status (e.g., Idle, Connect, Active, OpenSent, OpenConfirm, Established)
*   AS numbers
*   Uptime of BGP sessions
*   Number of prefixes received, advertised, and accepted
*   BGP routing table information
*   Error messages or status codes related to BGP operations

Interpreting the output requires familiarity with BGP concepts and terminology.
