#	--ospf_agg_dump [all | dip], [all | seg_id], [all | ip_fam (v4 | v6)]

##	Description
This command dumps the OSPF (Open Shortest Path First) Aggregate table. The OSPF aggregate table is used in route summarization, allowing multiple OSPF routes to be condensed into a single summary advertisement. This helps to reduce the size of the routing table and the amount of routing update traffic on the network.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` or `dip` | Filters the output. `all` displays all entries. `dip` likely refers to a specific destination IP address or prefix, though the exact behavior for `dip` would require further clarification or testing. |
| `all` or `seg_id` | Filters the output by segment ID. `all` displays entries for all segments. `seg_id` would filter for a specific segment. |
| `all` or `ip_fam (v4 | v6)` | Filters the output by IP family. `all` displays both IPv4 and IPv6 entries. `v4` displays only IPv4 entries. `v6` displays only IPv6 entries. |

##  Example usage
```
example_com:velocli> debug --ospf_agg_dump
Address   Masklen  Tag  Metric  MetricType  NoAdv  RefCnt  Marker
Marker decode: 0 - NOT_MARKED, 1 - MARKED_PRESENT, 2 - MARKED_UPDATE

example_com:velocli>
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The IP address of the aggregate route. |
| Masklen | The prefix length (subnet mask) for the aggregate route. |
| Tag | An optional OSPF route tag associated with the aggregate route. |
| Metric | The OSPF cost (metric) assigned to this aggregate route. |
| MetricType | The OSPF metric type for the aggregate route (e.g., Type 1 or Type 2 for external routes). |
| NoAdv | Indicates if the aggregate route is not advertised (No Advertise). |
| RefCnt | Reference Count, likely indicating how many component routes are summarized by this aggregate. |
| Marker | An internal marker used by the system for processing aggregate routes. <br> `0 - NOT_MARKED`: The entry is not marked. <br> `1 - MARKED_PRESENT`: The entry is marked as present. <br> `2 - MARKED_UPDATE`: The entry is marked for an update. |