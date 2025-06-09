#	--cluster_static_routes [[all | prefix] [all | segment-id] [all | v4 | v6]]

##	Description
Displays the static routes configured for a VeloCloud Edge cluster. These routes are typically used in High Availability (HA) configurations or hub clusters to ensure consistent routing for traffic traversing the cluster. The output includes details about the destination, next hop, and various route attributes.

##  Arguments (optional)
| Argument     | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `all`        | Shows all cluster static routes (default if no arguments are specified).    |
| `prefix`     | Filters the output to display routes matching a specific IP prefix.         |
| `segment-id` | Filters the output to display routes belonging to a specific segment ID.    |
| `v4`         | Displays only IPv4 cluster static routes.                                   |
| `v6`         | Displays only IPv6 cluster static routes.                                   |

If no arguments are provided, the command defaults to displaying all cluster static routes for all segments and both IPv4 and IPv6.

##  Example usage
```
example_com:velocli> debug --cluster_static_routes
Address   Netmask  Type  Gateway  Next Hop ID  Dst LogicalId  Metric  Preference  Flags  Vlan  Intf  MTU  SEG
P - PG, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS
```

##  Field descriptions
| Column        | Description                                                                                                |
|---------------|------------------------------------------------------------------------------------------------------------|
| Address       | The destination IP address for the static route.                                                           |
| Netmask       | The subnet mask for the destination IP address.                                                            |
| Type          | The type of the route. (The example output does not show specific types, but it would correspond to the flags legend if applicable). |
| Gateway       | The gateway IP address or interface for the route.                                                         |
| Next Hop ID   | The logical ID of the next hop device or entity.                                                           |
| Dst LogicalId | The logical ID of the destination.                                                                         |
| Metric        | The metric value associated with the route, used in route selection.                                       |
| Preference    | The administrative distance or preference value for the route. Lower values are generally preferred.       |
| Flags         | Various flags indicating the properties or origin of the route. See the legend below for details.          |
| Vlan          | The VLAN ID associated with the route, if applicable.                                                      |
| Intf          | The interface through which this route is learned or applied.                                              |
| MTU           | The Maximum Transmission Unit for the path associated with this route.                                     |
| SEG           | The Segment ID to which this route belongs.                                                                |

**Flags Legend:**
*   **P**: PG (Partner Gateway)
*   **D**: DCE (Dynamic Cost Edge - an internal VeloCloud term, likely related to dynamic path selection)
*   **L**: LAN SR (LAN Static Route)
*   **C**: Connected (Directly connected network)
*   **O**: External (Learned from an external routing protocol, e.g., OSPF, BGP)
*   **W**: WAN SR (WAN Static Route)
*   **S**: SecureEligible (Eligible for secure VeloCloud paths)
*   **R**: Remote (Route learned from a remote VeloCloud peer)
*   **s**: self (Route originated by the local Edge)
*   **r**: recursive (Recursive route, points to another route for resolution)
*   **H**: HA (High Availability related route)
*   **m**: Management (Management interface route)
*   **v**: ViaVeloCloud (Route learned via the VeloCloud overlay)
*   **A**: RouterAdvertisement (Learned via IPv6 Router Advertisement)
*   **c**: CWS (Cloud Web Security - now known as CSS or Cloud Security Service)
*   **a**: RAS (Remote Access Service)