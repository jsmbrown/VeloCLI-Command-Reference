#	--bgp_agg_dump [[all | <destination_ip_prefix>] [all | <segment_id>] [all | v4 | v6]]



##	Description
Dumps the BGP (Border Gateway Protocol) aggregate view from the VeloCloud Edge. BGP route aggregation is a mechanism to consolidate multiple specific BGP routes into a single, more general route advertisement. This process helps to reduce the size of BGP routing tables, improving overall routing stability and efficiency. This command displays the current state of these aggregate routes as known by the Edge.

The arguments are positional and optional.
- The first argument filters by destination IP prefix.
- The second argument filters by segment ID.
- The third argument filters by IP version (IPv4 or IPv6).

##  Arguments (optional)
The command accepts up to three positional arguments. If no arguments are provided, or `all` is used for a position, it defaults to displaying all entries for that category.

| Argument Value | Description |
|---|---|
| `all` | When used in any argument position, it signifies no filtering for that category (destination prefix, segment ID, or IP version). This is the default if an argument is omitted for a given position. |
| `<destination_ip_prefix>` | (Positional: 1st argument) Filters the output by the specified destination IP prefix. The prefix must be in CIDR notation (e.g., `192.168.1.0/24`). If an IP address is provided without a mask (e.g., `10.1.1.1`), it defaults to a `/32` mask for IPv4 and `/128` for IPv6. |
| `<segment_id>` | (Positional: 2nd argument) Filters the output by the specified VeloCloud segment ID. |
| `v4` | (Positional: 3rd argument) Displays only IPv4 BGP aggregate entries. |
| `v6` | (Positional: 3rd argument) Displays only IPv6 BGP aggregate entries. |

##  Example usage
Display all BGP aggregate entries:
```
example_com:velocli> debug --bgp_agg_dump
Segment   Address  Masklen  AS-set  Summary-only  Marker  RefCnt
1         10.0.0.0       8    True          True       1       5
Marker decode: 0 - NOT_MARKED, 1 - MARKED_PRESENT, 2 - MARKED_UPDATE
```

Display IPv4 BGP aggregate entries for the prefix `10.0.0.0/8` within segment `1`:
```
example_com:velocli> debug --bgp_agg_dump 10.0.0.0/8 1 v4
Segment   Address  Masklen  AS-set  Summary-only  Marker  RefCnt
1         10.0.0.0       8    True          True       1       5
Marker decode: 0 - NOT_MARKED, 1 - MARKED_PRESENT, 2 - MARKED_UPDATE
```

##  Field descriptions
| Column | Description |
|---|---|
| Segment | The segment ID to which the BGP aggregate route belongs. Segments are used for network segmentation within the VeloCloud SD-WAN. |
| Address | The network address of the BGP aggregate route. |
| Masklen | The prefix length (e.g., `24` for a `/24` subnet mask) of the BGP aggregate address. |
| AS-set | Indicates whether the `AS_SET` attribute is included with the aggregate route. The `AS_SET` attribute is a BGP path attribute that lists all AS numbers in the paths of the more specific routes that have been aggregated. Typically displayed as `True` or `False`. |
| Summary-only | Specifies if this aggregate route is advertised as "summary-only". If `True`, the more specific routes that contribute to this aggregate are suppressed from being advertised further to BGP peers. |
| Marker | An internal marker status for the aggregate entry, used for internal processing or state tracking. The meaning of the marker values is provided in the command output: <br> `0`: NOT_MARKED <br> `1`: MARKED_PRESENT <br> `2`: MARKED_UPDATE |
| RefCnt | Reference Count. This likely indicates the number of more specific routes that are currently being summarized by this aggregate entry. |
