# `debug --ospf_view [[all | <destination_ip>] [all | v4 | v6] [all | <segment_id>]]`

## Description
Displays the OSPF (Open Shortest Path First) routing information known to the VeloCloud Edge. This includes learned routes, their metrics, types, and status within specified segments or IP families.

## Arguments (optional)
The command `debug --ospf_view` can be run without arguments to display all OSPF view entries. Alternatively, you can provide up to three positional arguments to filter the output:

| Argument         | Description                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `destination_ip` | Optional. Filters the output by a specific destination IP address. Use `all` (or omit) to display routes for all destination IPs.         |
| `ip_family`      | Optional. Filters the output by IP address family. Valid values are `v4` (for IPv4) or `v6` (for IPv6). Use `all` (or omit) for both.       |
| `segment_id`     | Optional. Filters the output by a specific VeloCloud segment ID. Use `all` (or omit) to display routes across all relevant segments.        |

If arguments are omitted, they default to `all`. For example, `debug --ospf_view` is equivalent to `debug --ospf_view all all all`.

## Example Usage
```
example_com:velocli> debug --ospf_view
Address   Netmask  Gateway  Nbr IP  Nbr ID  Metric  OSPF Cost  Preference  Type  Intf  Synced  Advertise  Inbound  Tag  Reachable  Ptr  Age  Seg
O - Intra Area, IA - Inter Area, OE1 - External 1, OE2 - External 2

example_com:velocli>
```
*(Note: The example output above is a template. Actual output will contain OSPF route entries if OSPF is configured and active.)*

## Field Descriptions
| Column      | Description                                                                                                                               |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `Address`   | The destination network IP address for the OSPF route.                                                                                      |
| `Netmask`   | The subnet mask for the destination network.                                                                                                |
| `Gateway`   | The next-hop IP address to reach the destination network. This is typically an IP address on a directly connected OSPF neighbor.            |
| `Nbr IP`    | The IP address of the OSPF neighbor from which this route was learned.                                                                      |
| `Nbr ID`    | The OSPF Router ID of the neighbor advertising this route.                                                                                  |
| `Metric`    | The VeloCloud system's internal metric for the route. This may be influenced by factors beyond OSPF cost, especially if redistributed.     |
| `OSPF Cost` | The standard OSPF cost associated with this route to reach the destination.                                                                 |
| `Preference`| The administrative distance or preference value for this OSPF route. Lower values are more preferred.                                       |
| `Type`      | The OSPF route type. Common types include: <br> `O` - Intra Area <br> `IA` - Inter Area <br> `OE1` - External Type 1 <br> `OE2` - External Type 2 |
| `Intf`      | The local interface on the VeloCloud Edge through which this OSPF route was learned or is advertised.                                       |
| `Synced`    | Indicates if this OSPF route is synchronized with the VeloCloud overlay routing table (e.g., VCRP). (`True`/`False` or similar indication). |
| `Advertise` | Indicates if the VeloCloud Edge is advertising this route to its OSPF neighbors. (`True`/`False` or similar indication).                    |
| `Inbound`   | Indicates if the route was learned via OSPF from a neighbor (inbound). (`True`/`False` or similar indication).                              |
| `Tag`       | An optional OSPF route tag value associated with the route, often used for policy implementation or route filtering.                        |
| `Reachable` | Indicates whether the OSPF next-hop or destination is currently considered reachable. (`True`/`False` or similar indication).               |
| `Ptr`       | An internal system pointer or reference, generally not for direct user interpretation.                                                      |
| `Age`       | The age of the Link State Advertisement (LSA) in seconds from which this route information was derived.                                     |
| `Seg`       | The VeloCloud segment ID to which this OSPF route belongs or is associated.                                                                 |

**Note on Route Types:** The legend for OSPF route types (`O`, `IA`, `OE1`, `OE2`) is typically displayed in the command output as shown in the example.