#	--remote_routes [all|prefix] [all|segment-id] [all|v4|v6] [all|dest-logical-id]

##	Description
Displays the VeloCloud remote route table. This table contains routes learned from other VeloCloud Edges or Gateways through the VeloCloud Routing Protocol (VCRP). These routes represent networks reachable through the SD-WAN overlay.

Refer to the [VeloCloud SD-WAN Routing Overview](https://techdocs.broadcom.com/us/en/vmware-sde/velocloud-sase/vmware-velocloud-sd-wan/6-2/sd-wan-administration-guide/overview-3-admin/vmware-sd-wan-routing-overview-admin.html) for more details on routing concepts and flag meanings.

##  Arguments (optional)
Arguments can be used to filter the output. If no arguments are specified, all remote routes are displayed.

| Argument | Description |
|---|---|
| `all` (default for prefix) | Displays routes for all network prefixes. |
| `prefix` | Filters the output to display routes for a specific network prefix (e.g., 192.168.100.0/24). |
| `all` (default for segment-id) | Displays routes across all segments. |
| `segment-id` | Filters the output to display routes belonging to a specific segment ID. |
| `all` (default for address family) | Displays routes for both IPv4 and IPv6 address families. |
| `v4` | Displays only IPv4 remote routes. |
| `v6` | Displays only IPv6 remote routes. |
| `all` (default for dest-logical-id) | Displays routes from all destination logical IDs. |
| `dest-logical-id` | Filters the output to display routes destined for a specific VeloCloud Edge or Gateway, identified by its logical ID. |

##  Example usage
```
example_com:velocli> debug --remote_routes
Address   Netmask  Type  Gateway  Next Hop ID  Dst LogicalId  Metric  Preference  Flags  Vlan  Intf  MTU  SEG
P - PG, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS
```
*(Note: The example above shows the command and the header output. Actual execution would list the remote routes matching the criteria.)*

##  Field descriptions
| Column | Description |
|---|---|
| Address | The network address of the remote prefix. |
| Netmask | The subnet mask for the remote network address. |
| Type | Indicates how the route was learned or its characteristics within the VeloCloud overlay. For remote routes, this typically signifies it was learned via VCRP from a peer. |
| Gateway | The gateway for this route. For overlay routes, this is often 'any' as the actual path selection is dynamic. |
| Next Hop ID | The logical ID of the VeloCloud Edge or Gateway that advertised this route. This is the next hop within the SD-WAN overlay. |
| Dst LogicalId | The logical ID of the VeloCloud Edge or Gateway that is the ultimate destination or owner of this prefix. |
| Metric | The metric associated with the route, used by VCRP for path selection. Lower metrics are generally preferred. |
| Preference | The administrative preference value for the route. This can influence route selection when multiple sources provide the same prefix. |
| Flags | Various flags providing additional information about the route. See the legend output by the command for specific flag meanings: <br> `P` - PG (Partner Gateway) <br> `D` - DCE (Dynamic Cost Edge) <br> `L` - LAN SR (LAN Static Route) <br> `C` - Connected <br> `O` - External (e.g., OSPF, BGP learned) <br> `W` - WAN SR (WAN Static Route) <br> `S` - SecureEligible (Eligible for secure VeloCloud paths) <br> `R` - Remote (Learned from another VeloCloud device) <br> `s` - self (Route originated by this Edge) <br> `r` - recursive (Recursive route lookup) <br> `H` - HA (High Availability related) <br> `m` - Management (Management interface route) <br> `v` - ViaVeloCloud (Route accessible via the VeloCloud overlay) <br> `A` - RouterAdvertisement (Learned via IPv6 RA) <br> `c` - CWS (Cloud Web Security / CSS related) <br> `a` - RAS (Remote Access User) |
| Vlan | The VLAN ID associated with the route on the source/destination Edge, if applicable. |
| Intf | The interface associated with the route on the source/destination Edge. |
| MTU | The Maximum Transmission Unit for the path to this remote network. |
| SEG | The Segment ID to which this route belongs. Segmentation allows for logical partitioning of the network. |