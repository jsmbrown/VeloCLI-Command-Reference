#	--local_routes [[all | prefix] [all | segment-id] [all | v4 | v6]]

##	Description
Displays the VeloCloud Edge's local route table. This table includes routes learned from connected LAN segments, static routes configured on the Edge, and routes for VeloCloud services. It shows how the Edge will route traffic originating from or destined to its local interfaces before SD-WAN policies are applied.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` (default if no prefix specified) | Display all local routes. |
| `prefix` | Filter routes by a specific IP prefix (e.g., 192.168.1.0/24). |
| `all` (default if no segment-id specified) | Display routes for all segments. |
| `segment-id` | Filter routes by a specific segment ID. |
| `all` (default if no IP version specified) | Display routes for both IPv4 and IPv6. |
| `v4` | Display only IPv4 routes. |
| `v6` | Display only IPv6 routes. |

##  Example usage
```
example_com:velocli> debug --local_routes
Address                Netmask   Type              Gateway                           Next Hop ID                         Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  MTU  SEG
192.168.88.1   255.255.255.255    any                  any                                   N/A                                   N/A       True       0           0     CS     0   LO1  N/A    0
172.30.0.6     255.255.255.255    any                  any                                   N/A                                   N/A       True       0           0     Ss     0   GE1  N/A    0
172.30.0.0       255.255.255.0    any                  any                                   N/A                                   N/A       True       3           0     CS     0   GE1  N/A    0
0.0.0.0                0.0.0.0  cloud        216.221.31.44  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any  N/A    0
0.0.0.0                0.0.0.0  cloud           172.30.0.1                                   N/A                                   N/A       True       3           0      S     0   GE1  N/A    0
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The destination IP address or network prefix. |
| Netmask | The subnet mask for the destination network. |
| Type | The type of route. Common types include: `any` (often for local interface routes), `cloud` (routes related to VeloCloud Gateways or services). |
| Gateway | The IP address of the next-hop gateway for this route. Can be 'any' if it's a directly connected network or a VeloCloud specific path. |
| Next Hop ID | The VeloCloud logical identifier for the next hop, typically applicable for routes traversing the SD-WAN overlay. 'N/A' if not applicable. |
| Dst LogicalId | The VeloCloud logical identifier for the final destination, if known. 'N/A' if not applicable. |
| Reachable | Indicates whether the destination is currently considered reachable (True/False). |
| Metric | The cost associated with this route. Lower metrics are generally preferred. |
| Preference | A value used to determine the preference of a route when multiple routes to the same destination exist. Lower values are more preferred. |
| Flags | Various flags providing more information about the route. Common flags include: `C` (Connected), `S` (Static), `s` (Self), `v` (Via VeloCloud). The exact meaning of all flags can be found in VeloCloud's routing documentation. |
| Vlan | The VLAN ID associated with this route, if applicable. |
| Intf | The local interface out of which traffic for this route will be sent (e.g., GE1, LO1, any). |
| MTU | The Maximum Transmission Unit for the path. 'N/A' if not applicable or not determined. |
| SEG | The Segment ID to which this route belongs. |