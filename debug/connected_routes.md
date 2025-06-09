# `debug --connected_routes`

## Description
Displays routes for networks directly connected to the VeloCloud Edge interfaces. These routes are fundamental to the VeloCloud Routing Protocol (VCRP) and represent the local networks accessible via the Edge.

## Arguments (optional)
The command can be run without arguments to display all connected routes. Alternatively, you can filter the output using the following arguments:

| Argument         | Description                                                                                                |
|------------------|------------------------------------------------------------------------------------------------------------|
| `all` or `prefix`  | Specifies the IP prefix to filter by (e.g., `192.168.1.0/24`). Use `all` or omit to show all prefixes.      |
| `all` or `segment-id` | Specifies the segment ID to filter by. Use `all` or omit to show routes for all segments.                 |
| `all` or `v4` or `v6` | Specifies the IP address family to display (`v4` for IPv4, `v6` for IPv6). Use `all` or omit for both. |

## Example Usage
```
example_com:velocli> debug --connected_routes
Address                Netmask  Type  Gateway  Next Hop ID  Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  MTU  SEG
192.168.88.1   255.255.255.255   any      any          N/A            N/A       True       0           0     CS     0   LO1  N/A    0
172.30.0.0       255.255.255.0   any      any          N/A            N/A       True       3           0     CS     0   GE1  N/A    0
1.2.3.4        255.255.255.255   any      any          N/A            N/A       True       0           0     CS     0   LO2  N/A    1
172.30.1.0       255.255.255.0   any      any          N/A            N/A       True       0           0     CS     0   GE2  N/A    1
172.30.0.0       255.255.255.0   any      any          N/A            N/A       True       3           0     CS     0   GE1  N/A    1
```

## Field Descriptions
| Column        | Description                                                                                                |
|---------------|------------------------------------------------------------------------------------------------------------|
| Address       | The IP address of the connected network or host.                                                           |
| Netmask       | The subnet mask for the address.                                                                           |
| Type          | For connected routes, this is typically `any`, indicating a directly connected network.                    |
| Gateway       | For connected routes, this is typically `any`, as the network is directly attached.                        |
| Next Hop ID   | Not Applicable (`N/A`) for directly connected routes.                                                      |
| Dst LogicalId | Destination Logical ID. Not Applicable (`N/A`) for directly connected routes.                              |
| Reachable     | Indicates if the connected network is currently reachable (`True` or `False`).                               |
| Metric        | The administrative distance or cost associated with this route. For connected routes, this is typically 0. |
| Preference    | VeloCloud specific route preference value.                                                                 |
| Flags         | Route flags providing additional information. Common flags include: <br> `C` - Connected <br> `S` - SecureEligible (can be advertised over SD-WAN tunnels) <br> (See legend below for more flags) |
| Vlan          | The VLAN ID associated with the interface if applicable. `0` typically means untagged or default VLAN.     |
| Intf          | The local Edge interface (e.g., `GE1`, `LO1`) to which this network is connected.                          |
| MTU           | Maximum Transmission Unit. `N/A` indicates it may use the interface's default or is not specified here.    |
| SEG           | The Segment ID to which this connected route belongs. Network segmentation allows for traffic isolation.   |

**Route Flags Legend:**
P - PG (Partner Gateway), B - BGP, D - DCE (Dynamic Cost Egress), L - LAN SR (Static Route), C - Connected, O - External (OSPF), W - WAN SR (Static Route), S - SecureEligible, R - Remote, s - self, r - recursive, H - HA (High Availability), m - Management, n - nonVelocloud, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS (Cloud Web Security), a - RAS (Remote Access Server), M - MTGRE (Multi-hop GRE), g - Global PG Static, b - Blackhole, I - IPSec, G - GRE, p - Peer