#	--route_stats [src_id] [all | nhop_id] [all | seg] [all | route_type]

##	Description
Requests and displays route statistics. Statistics can be filtered for routes originated by a specific `src_id`, associated with a particular `nhop_id` (next hop ID), belonging to a given `seg` (segment), and matching a certain `route_type`.

##	Arguments (optional)
The arguments are positional. If an argument is omitted, it defaults to `all` or its broadest scope, and subsequent arguments must also be omitted or their default values will be used.

| Argument          | Description                                                                                                                               |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `src_id`          | (Optional) The identifier of the source that originated the routes. If this argument is omitted, statistics for all relevant sources are typically displayed. |
| `all` \| `nhop_id`  | (Optional) Filters statistics by the next hop ID. Specify the literal keyword `all` to include routes regardless of their next hop ID, or provide a specific `nhop_id`. Defaults to `all` if omitted. |
| `all` \| `seg`      | (Optional) Filters statistics by segment ID. Specify the literal keyword `all` to include routes from all segments, or provide a specific `seg` (segment ID). Defaults to `all` if omitted. |
| `all` \| `route_type`| (Optional) Filters statistics by route type. Specify the literal keyword `all` to include all types of routes, or provide a specific `route_type`. Defaults to `all` if omitted. |

##	Example usage
```
example_com:velocli> debug --route_stats
<Output showing route statistics, filtered according to any provided arguments, would be displayed here. The specific format of the output is not available.>
```

##	Field descriptions
| Column | Description |
|---|---|
|   |   |