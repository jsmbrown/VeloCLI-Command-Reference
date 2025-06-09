#	--dc_routes [all|prefix] [all|segment-id]

##	Description
Dumps the datacenter route table. This table contains routes learned from Hub Edges or Gateways that are designated as datacenters within the VeloCloud SD-WAN overlay. These routes are typically advertised via VCRP (VeloCloud Routing Protocol) from these datacenter entities.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` or `prefix` | Filters the output. `all` displays all datacenter routes. `prefix` allows you to specify a particular IP prefix (e.g., 192.168.100.0/24) to display routes for. |
| `all` or `segment-id` | Filters the output by segment. `all` displays routes across all segments. `segment-id` allows you to specify a particular segment ID to display routes for that segment. |

##  Example usage
```
example_com:velocli> debug --dc_routes
Address   Netmask  Type  Gateway  Next Hop ID  Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  MTU
P - PG, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, n - nonVelocloud, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS, I - IPSec, G - GRE
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The destination IP address for the route. |
| Netmask | The subnet mask for the destination IP address. |
| Type | The type of route. This indicates how the route was learned or its nature within the SD-WAN fabric (e.g., connected, static, BGP). |
| Gateway | The gateway or next-hop IP address for this route. For overlay routes, this might be 'any' or a specific underlay IP. |
| Next Hop ID | The logical identifier of the next hop VeloCloud Edge or Gateway. |
| Dst LogicalId | The logical identifier of the destination VeloCloud Edge or Gateway. |
| Reachable | Indicates whether the destination is currently reachable (True/False). |
| Metric | A value used by routing protocols to determine the best path to a destination. Lower metrics are generally preferred. |
| Preference | A value indicating the trustworthiness or preference of the route source. Lower values are generally preferred. |
| Flags | Provides additional information about the route. See the legend below the table in the example output for specific flag meanings. |
| Vlan | The VLAN ID associated with this route, if applicable. |
| Intf | The interface associated with this route. |
| MTU | The Maximum Transmission Unit for the path associated with this route. |

**Flags Legend:**
*   **P**: PG (Partner Gateway)
*   **D**: DCE (Dynamic Cost Exchange - an internal VeloCloud mechanism)
*   **L**: LAN SR (LAN Static Route)
*   **C**: Connected
*   **O**: External (Typically OSPF or BGP learned routes redistributed into VeloCloud)
*   **W**: WAN SR (WAN Static Route)
*   **S**: SecureEligible (Eligible for secure VeloCloud tunnels)
*   **R**: Remote (A route learned from another VeloCloud device)
*   **s**: self (A route originating from the local Edge)
*   **r**: recursive (A route that requires a recursive lookup)
*   **H**: HA (High Availability related route)
*   **m**: Management (Route related to management traffic)
*   **n**: nonVelocloud (Route to a Non-VeloCloud Site/NSD)
*   **v**: ViaVeloCloud (Route learned via the VeloCloud overlay)
*   **A**: RouterAdvertisement (Learned via IPv6 Router Advertisement)
*   **c**: CWS (Cloud Web Security / CSS related route)
*   **a**: RAS (Remote Access User related route)
*   **I**: IPSec (Route learned via an IPSec tunnel to an NVS/NSD)
*   **G**: GRE (Route learned via a GRE tunnel to an NVS/NSD)