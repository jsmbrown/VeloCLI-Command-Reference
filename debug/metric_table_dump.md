#	`--metric_table_dump` `[all|logical_id] [all|segment-id]`

##	Description
Dumps the transit metric table from the VeloCloud Edge. This table contains a list of peers and the associated VeloCloud Routing Protocol (VCRP) metric values that will be used in the overlay.  These values also map to the BGP metric that will be used by a destination peer edge or gateway when advertising prefixes learned from the edge. These metrics help determine the optimal paths for traffic to various destinations.

##	Arguments (optional)
The command accepts two optional positional arguments. If an argument is omitted, it defaults to `all`.

| Argument Position | Value        | Description                                                                                                |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------|
| 1st               | `all`        | (Default if omitted) Display metrics for all destination logical IDs.                                      |
| 1st               | `logical_id` | Display metrics for the specified destination peer edge/gateway logical ID. |
| 2nd               | `all`        | (Default if omitted) Display metrics across all configured network segments.                               |
| 2nd               | `segment-id` | Display metrics for the specified segment ID. |

##	Example usage
```
example_com:velocli> debug --metric_table_dump
[
  {
    "LogicalID": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8",
    "NextHop": [
      {
        "Metric": 81,
        "NextHopLogicalID": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8"
      }
    ],
    "SegmentID": 2
  }
]
```

##	Field descriptions
| Field          | Description                                                                                                                                                              |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LogicalID`    | UUID of the destination peer (e.g., another VeloCloud Edge, Hub, Gateway, or Non-VeloCloud Site) for which transit metrics are being reported.          |
| `NextHop`      | An array of the UUID and next metric for the applicable next hop. |
| `NextHop.Metric` | VCRP metric of the overlay route/BGP metric value that the destination peer will use when advertising prefixes from the source edge. |
| `NextHop.NextHopLogicalID` | UUID of the next hop edge/gateway peer used to reach the destination peer. |
| `SegmentID` | Segment to which the metric value is applicable. |