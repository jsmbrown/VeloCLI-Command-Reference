#	--bgp_view_summary [v4 | v6 | all]

##	Description
Summary of BGP configuration and neighbor states

##  Arguments (optional)
| Argument | Description |
|---|---|
| none (or 'all') | Display all BGP neighbors |
| v4 | Display only IPv4 neighbors |
| v6 | Display only IPv6 neighbors |

##  Example usage
```
example_com:velocli> debug --bgp_view_summary
sh bgp vrf all summary
======================

Instance [vc:0:1]:

IPv4 Unicast Summary:

BGP view name [vc:0:1]
BGP router identifier 172.16.44.2, local AS number 65004 vrf-id 1
BGP table version 7
RIB entries 13, using 2496 bytes of memory
Peers 1, using 22 KiB of memory

Neighbor        V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd      PfxSnt
192.168.10.202  4      65005     10192      8929        0    0    0 6d04h43m            5           3

Total number of neighbors 1

IPv6 Unicast Summary:

BGP view name [vc:0:1]
BGP router identifier 172.16.44.2, local AS number 65004 vrf-id 1
BGP table version 0
RIB entries 0, using 0 bytes of memory
Peers 1, using 22 KiB of memory

Neighbor            V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd      PfxSnt
fd52:6cbf:1d43::2:2 4      65505         0         0        0    0    0    never         Idle           

Total number of neighbors 1
```

##  Field descriptions
| Column | Description |
|---|---|
| Neighbor | BGP neighbor IP address |
| AS | Autonomous system number of the BGP neighbor |
| MsgRcvd | Count of BGP messages received from neighbor |
| MsgSent | Count of BGP messages sent to neighbor |
| Up/Down | Time since last up/down state change |
| State/PfxRcd | BGP neighbor state if not established, otherwise displays qty of prefixes received from neighbor |
| PfxSnt | Quantity of prefixes advertised to BGP neighbor |