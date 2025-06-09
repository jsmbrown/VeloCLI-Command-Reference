#	--bgp_redis_dump [[all | dip <prefix/length>] [all | <segment_id>] [all | v4 | v6]]

##	Description
This command dumps the BGP (Border Gateway Protocol) routing information as viewed from the Redis database. Redis is often used as an in-memory data store, and in this context, it holds BGP routing data that the VeloCloud Edge uses. This command is useful for troubleshooting BGP routing issues by inspecting the raw BGP data.

##  Arguments (optional)
The command accepts up to three optional positional arguments to filter the output. If no arguments are provided, it defaults to displaying all BGP Redis entries for all segments and both IPv4 and IPv6.

| Argument Position | Value                                 | Description                                                                                                                               |
|-------------------|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1                 | `all`                                 | (Default) Show entries for all destination IP prefixes.                                                                                   |
|                   | `dip <prefix/length>`                 | Show entries for a specific destination IP prefix. The prefix must be in CIDR notation (e.g., `192.168.1.0/24` or `2001:db8::/32`). If the length is omitted, it defaults to `/32` for IPv4 and `/128` for IPv6. |
| 2                 | `all`                                 | (Default) Show entries for all segment IDs.                                                                                               |
|                   | `<segment_id>`                        | Show entries for a specific segment ID (integer).                                                                                         |
| 3                 | `all`                                 | (Default) Show entries for both IPv4 and IPv6 address families.                                                                           |
|                   | `v4`                                  | Show entries for IPv4 address family only.                                                                                                |
|                   | `v6`                                  | Show entries for IPv6 address family only.                                                                                                |

##  Example usage
```
example_com:velocli> debug --bgp_redis_dump
Address                Netmask        Gateway         Nbr IP   Nbr ID  Metric  Redis Metric  Type  Intf  SEG  Communities        Flags
172.30.1.0       255.255.255.0            any            N/A  0.0.0.0       0             0     E   GE2    1                      0x90
172.31.0.0       255.255.255.0  172.30.255.36  172.30.255.36  0.0.0.0       0             0     E   any    1                 0x1000084
172.30.1.200   255.255.255.255            any            N/A  0.0.0.0       0             0     E   GE2    1                     0x480
172.30.0.6     255.255.255.255            any            N/A  0.0.0.0       0             0     E   GE1    1                     0x480
1.2.3.4        255.255.255.255            any            N/A  0.0.0.0       0             0     E   LO2    1               -0x7fffff70
```
```
example_com:velocli> debug --bgp_redis_dump dip 172.30.1.0/24 1 v4
Address                Netmask        Gateway         Nbr IP   Nbr ID  Metric  Redis Metric  Type  Intf  SEG  Communities        Flags
172.30.1.0       255.255.255.0            any            N/A  0.0.0.0       0             0     E   GE2    1                      0x90
```

##  Field descriptions
| Column         | Description                                                                                                |
|----------------|------------------------------------------------------------------------------------------------------------|
| Address        | The destination IP address prefix of the BGP route.                                                        |
| Netmask        | The subnet mask associated with the destination IP address prefix.                                           |
| Gateway        | The next-hop IP address for the route. Can be 'any' if the route is locally originated or directly connected. |
| Nbr IP         | The IP address of the BGP neighbor from which this route was learned. 'N/A' if not applicable.               |
| Nbr ID         | The BGP Router ID of the neighbor from which this route was learned. '0.0.0.0' if not applicable.            |
| Metric         | The BGP Multi-Exit Discriminator (MED) or other metric associated with the route.                            |
| Redis Metric   | The metric value as stored in the Redis database, potentially an internal representation.                    |
| Type           | The type of BGP route. Common types include 'E' for eBGP (External BGP) and 'I' for iBGP (Internal BGP).   |
| Intf           | The interface associated with this BGP route on the VeloCloud Edge.                                          |
| SEG            | The Segment ID to which this route belongs. Segments are used for network segmentation within the SD-WAN.    |
| Communities    | BGP communities associated with the route. These are used for tagging routes and applying policies.        |
| Flags          | Internal flags associated with the BGP route, represented in hexadecimal format.                             |