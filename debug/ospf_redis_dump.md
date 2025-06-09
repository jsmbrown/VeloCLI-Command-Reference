#	--ospf_redis_dump [[all | dip <prefix/length>] [all | v4 | v6] [all | <segment-id>]]

##	Description
This command dumps the OSPF (Open Shortest Path First) routing information as viewed or stored by the VeloCloud Edge's internal Redis database. This can be useful for diagnosing OSPF routing issues and understanding how OSPF routes are being processed by the Edge.

The command allows filtering the output based on specific prefixes, IP version (IPv4 or IPv6), and segment ID.

##	Arguments (optional)
The arguments are positional and optional. If no arguments are provided, the command defaults to displaying all OSPF routes (equivalent to `all all all`).

| Argument Position | Value                     | Description                                                                                                                               |
|-------------------|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1                 | `all`                     | (Default) Displays all OSPF routes.                                                                                                       |
|                   | `dip <prefix/length>`     | Displays OSPF routes matching the specified IP prefix and length (e.g., `dip 192.168.1.0/24` or `dip 2001:db8::/32`).                      |
| 2                 | `all`                     | (Default) Displays routes for both IPv4 and IPv6.                                                                                         |
|                   | `v4`                      | Displays only IPv4 OSPF routes.                                                                                                           |
|                   | `v6`                      | Displays only IPv6 OSPF routes.                                                                                                           |
| 3                 | `all`                     | (Default) Displays routes across all segments.                                                                                            |
|                   | `<segment-id>`            | Displays routes only for the specified segment ID (an integer).                                                                           |

##	Example usage
```
example_com:velocli> debug --ospf_redis_dump
Address   Netmask  Gateway  Nbr IP  Nbr ID  Metric  Redis Metric  OSPF Cost  Type  Intf  Flags  Seg
```
To display OSPF routes for a specific IPv4 prefix in segment 1:
```
example_com:velocli> debug --ospf_redis_dump dip 10.50.0.0/16 v4 1
Address   Netmask  Gateway  Nbr IP  Nbr ID  Metric  Redis Metric  OSPF Cost  Type  Intf  Flags  Seg
10.50.0.0 255.255.0.0 192.168.10.2 192.168.10.2 10.0.0.5 10 10 10 O GE3 - 1
```

##	Field descriptions
| Column       | Description                                                                                                |
|--------------|------------------------------------------------------------------------------------------------------------|
| Address      | The destination network IP address of the OSPF route.                                                      |
| Netmask      | The subnet mask for the destination network.                                                               |
| Gateway      | The next-hop IP address to reach the destination network.                                                  |
| Nbr IP       | The IP address of the OSPF neighbor from which this route was learned.                                     |
| Nbr ID       | The OSPF Router ID of the advertising neighbor.                                                            |
| Metric       | The OSPF metric (cost) associated with the route as advertised by the neighbor.                            |
| Redis Metric | The metric value for this route as stored in the Edge's Redis view, potentially after VeloCloud processing.  |
| OSPF Cost    | The original OSPF cost of the route.                                                                       |
| Type         | The OSPF route type. See legend below.                                                                     |
| Intf         | The VeloCloud Edge interface through which this OSPF route was learned or is reachable.                    |
| Flags        | Flags associated with the OSPF route (specific VeloCloud or OSPF attributes).                              |
| Seg          | The segment ID to which this OSPF route belongs.                                                           |

**Route Type Legend:**
*   `O` - Intra Area: A route to a destination within the same OSPF area.
*   `IA` - Inter Area: A route to a destination in another OSPF area.
*   `OE1` - External Type 1: An external route where the metric is the sum of the external cost and the internal cost to the ASBR.
*   `OE2` - External Type 2: An external route where the metric is solely the external cost, and the internal cost to the ASBR is not considered for path selection unless external costs are equal.