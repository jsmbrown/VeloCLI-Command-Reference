#	--unique_routes [[all | prefix] [all | segment-id] [all | v4 | v6]]

##	Description
Displays the VeloCloud Edge's unique unified route table. This command aggregates routes to the same destination prefix, showing a single entry for each unique prefix and indicating the number of available next hops for it. This provides a summarized view compared to the `--routes` command, which lists all individual paths.

##  Arguments (optional)
The arguments are positional and optional. If an argument is omitted, it defaults to 'all'.

| Argument     | Description                                                                                                |
|--------------|------------------------------------------------------------------------------------------------------------|
| `all`        | Keyword used as a placeholder or to explicitly request all entries for the corresponding filter.           |
| `prefix`     | Filters the output to display routes matching a specific network prefix (e.g., `192.168.1.0/24` or `0.0.0.0`). |
| `segment-id` | Filters the output by a specific segment ID (a numerical identifier).                                      |
| `v4`         | Filters the output to display only IPv4 routes.                                                            |
| `v6`         | Filters the output to display only IPv6 routes.                                                            |

##  Example usage
```
example_com:velocli> debug --unique_routes
Address                Netmask   Type              Gateway  Next Hop Name                           Next Hop ID  Destination Name                         Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  Sub IntfId  MTU  SEG  NH Count
0.0.0.0                0.0.0.0  cloud        216.221.31.44     vcg44-dfw1  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8        vcg44-dfw1  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any         N/A  N/A    0         2
172.30.0.0       255.255.255.0    any                  any            N/A                                   N/A               N/A                                   N/A       True       3           0     CS     0   GE1         N/A  N/A    0         1
172.30.0.6     255.255.255.255    any                  any            N/A                                   N/A               N/A                                   N/A       True       0           0     Ss     0   GE1         N/A  N/A    0         1
192.168.88.1   255.255.255.255    any                  any            N/A                                   N/A               N/A                                   N/A       True       0           0     CS     0   LO1         N/A  N/A    0         1
::                          ::  cloud  2605:a7c0:3:301::44     vcg44-dfw1  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8        vcg44-dfw1  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8      False     255           0      v     0   any         N/A  N/A    0         1
P - PG, B - BGP, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, n - nonVelocloud, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS, M - MTGRE, g - Global PG Static, b - Blackhole, I - IPSec, G - GRE, p - Peer
```

##  Field descriptions
| Column             | Description                                                                                                                               |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| Address            | The network address or IP address of the route destination.                                                                               |
| Netmask            | The subnet mask for the destination network.                                                                                              |
| Type               | The type of route (e.g., `cloud`, `edge2edge`, `connected`). Indicates how the route was learned or the nature of its destination.        |
| Gateway            | The IP address of the gateway for this route. Can be 'any' if not applicable (e.g., for connected routes).                                |
| Next Hop Name      | The descriptive name of the primary next hop (e.g., VeloCloud Gateway name, peer Edge name). 'N/A' if not applicable.                     |
| Next Hop ID        | The unique identifier (often a UUID) for the primary next hop. 'N/A' if not applicable.                                                   |
| Destination Name   | The descriptive name of the final destination entity (e.g., remote Edge, Gateway).                                                        |
| Dst LogicalId      | The logical identifier of the destination.                                                                                                |
| Reachable          | Indicates whether the destination prefix is currently considered reachable (`True` or `False`).                                           |
| Metric             | The routing metric associated with this route. Lower values are generally preferred.                                                      |
| Preference         | The administrative preference value for this route. Lower values indicate a more preferred route.                                         |
| Flags              | A set of flags providing additional information about the route. See the legend at the bottom of the example output for flag meanings.    |
| Vlan               | The VLAN ID associated with this route, if applicable.                                                                                    |
| Intf               | The local interface (e.g., `GE1`, `LO1`, `any`) through which this route is accessed.                                                     |
| Sub IntfId         | The sub-interface ID, if applicable. 'N/A' otherwise.                                                                                     |
| MTU                | The Maximum Transmission Unit for paths associated with this route. 'N/A' if not applicable or variable.                                  |
| SEG                | The Segment ID to which this route belongs.                                                                                               |
| NH Count           | Next Hop Count. The number of available next hops or paths for this unique destination prefix.                                            |

**Flag Legend:**
*   **P**: PG (Partner Gateway)
*   **B**: BGP (Border Gateway Protocol)
*   **D**: DCE (Dynamic Cost Edge - an older term, likely related to dynamic path selection)
*   **L**: LAN SR (LAN Static Route)
*   **C**: Connected
*   **O**: External (Learned from an external routing protocol like OSPF)
*   **W**: WAN SR (WAN Static Route)
*   **S**: SecureEligible (Eligible for secure VeloCloud paths)
*   **R**: Remote (Learned from a remote VeloCloud entity)
*   **s**: self (Route to the Edge itself)
*   **r**: recursive (Recursive route)
*   **H**: HA (High Availability)
*   **m**: Management (Management route)
*   **n**: nonVelocloud (Route to a Non-VeloCloud Site/NSD)
*   **v**: ViaVeloCloud (Route via the VeloCloud overlay)
*   **A**: RouterAdvertisement (Learned via IPv6 Router Advertisement)
*   **c**: CWS (Cloud Web Security - likely related to CSS)
*   **a**: RAS (Remote Access Site)
*   **M**: MTGRE (Multi-hop GRE tunnel)
*   **g**: Global PG Static (Global Partner Gateway Static Route)
*   **b**: Blackhole
*   **I**: IPSec (Route via an IPSec tunnel, typically to an NSD)
*   **G**: GRE (Route via a GRE tunnel, typically to an NSD)
*   **p**: Peer (Learned from a peer Edge, likely via DE2E)