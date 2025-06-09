#	--overlay_routes [all|prefix] [all|segment-id] [all|v4|v6]

##	Description
Displays the VeloCloud Routing Protocol (VCRP) route table, which contains routes learned from other VeloCloud Edges and Gateways within the SD-WAN overlay network. This command helps in understanding how traffic is routed across the overlay.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` (default) or `prefix` | Specifies whether to display all routes or filter by a specific IP prefix (e.g., `192.168.1.0/24`). If `prefix` is used, the actual prefix must follow. |
| `all` (default) or `segment-id` | Specifies whether to display routes for all segments or filter by a specific segment ID (e.g., `1`). If `segment-id` is used, the ID must follow. |
| `all` (default) or `v4` or `v6` | Specifies whether to display all routes, only IPv4 routes, or only IPv6 routes. |

##  Example usage
```
example_com:velocli> debug --overlay_routes
Address   Netmask   Type              Gateway                           Next Hop ID                         Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  MTU  SEG
0.0.0.0   0.0.0.0  cloud        216.221.31.44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    0
::             ::  cloud  2605:a7c0:3:301::44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    0
0.0.0.0   0.0.0.0  cloud        216.221.31.44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    1
::             ::  cloud  2605:a7c0:3:301::44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    1
0.0.0.0   0.0.0.0  cloud        216.221.31.44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    2
P - PG, B - BGP, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, n - nonVelocloud, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS, M - MTGRE, g - Global PG Static, b - Blackhole, I - IPSec, G - GRE, p - Peer
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The destination IP address (IPv4 or IPv6) for the overlay route. |
| Netmask | The subnet mask for the destination IP address. |
| Type | The type of overlay route. Common types include: `cloud` (route to a VeloCloud Gateway), `edge2edge` (route to a peer VeloCloud Edge), `hub` (route to a VeloCloud Hub Edge). |
| Gateway | The IP address of the next-hop VeloCloud Gateway or Edge for this overlay route. This is the underlay IP address of the remote peer. |
| Next Hop ID | The unique VeloCloud Logical ID of the immediate next-hop VeloCloud device (Edge or Gateway) for this route. |
| Dst LogicalId | The unique VeloCloud Logical ID of the final destination VeloCloud Edge or Gateway for this route. For direct paths, this is often the same as the Next Hop ID. |
| Reachable | Indicates whether the destination is currently reachable via the overlay path (`True` or `False`). |
| Metric | A cost associated with the route, used in path selection by VCRP. Lower values are generally preferred. |
| Preference | A numerical value indicating the preference of this route. Lower values are more preferred. This is influenced by Overlay Flow Control (OFC) settings and route source. |
| Flags | Single or multiple character flags providing additional information about the route. Common flags include: <br> `P` - PG (Partner Gateway) <br> `B` - BGP <br> `D` - DCE (Dynamic Cost Exchange) <br> `L` - LAN SR (Static Route) <br> `C` - Connected <br> `O` - External (e.g., OSPF) <br> `W` - WAN SR (Static Route) <br> `S` - SecureEligible <br> `R` - Remote <br> `s` - self <br> `r` - recursive <br> `H` - HA (High Availability) <br> `m` - Management <br> `n` - nonVelocloud (Non-VeloCloud Site) <br> `v` - ViaVeloCloud (Indicates a route learned via the VeloCloud overlay) <br> `A` - RouterAdvertisement <br> `c` - CWS (Cloud Web Security) <br> `a` - RAS (Remote Access Site) <br> `M` - MTGRE (Multi-hop GRE) <br> `g` - Global PG Static <br> `b` - Blackhole <br> `I` - IPSec <br> `G` - GRE <br> `p` - Peer |
| Vlan | The VLAN ID associated with the route on the LAN side, if applicable. For many overlay routes, this may be `0` or `any` if not specific to a particular LAN segment's VLAN. |
| Intf | The logical interface over which this route is learned or applied. For overlay routes, this is typically `any` as the route exists over dynamic tunnels rather than a fixed physical interface. |
| MTU | Maximum Transmission Unit for the path. `N/A` indicates that the MTU is not specifically set for this route entry or is determined dynamically. |
| SEG | The Segment ID to which this overlay route belongs. VeloCloud SD-WAN supports network segmentation, and routes can be specific to a segment. |