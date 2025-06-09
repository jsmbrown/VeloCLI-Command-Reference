#	`--metric_table_dump` `[all|logical_id] [all|segment-id]`

##	Description
Dumps the transit metric table from the VeloCloud Edge. This table contains cost metrics used by the Edge for path selection decisions within the SD-WAN overlay, particularly influencing Overlay Flow Control (OFC) and VeloCloud Routing Protocol (VCRP) behavior. These metrics help determine the optimal paths for traffic to various destinations.

##	Arguments (optional)
The command accepts two optional positional arguments. If an argument is omitted, it defaults to `all`.

| Argument Position | Value        | Description                                                                                                |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------|
| 1st               | `all`        | (Default if omitted) Display metrics for all destination logical IDs.                                      |
| 1st               | `logical_id` | Display metrics for the specified destination logical ID. This ID typically represents a peer VeloCloud Edge, Gateway, or a Non-VeloCloud Site (NVS/NSD). |
| 2nd               | `all`        | (Default if omitted) Display metrics across all configured network segments.                               |
| 2nd               | `segment-id` | Display metrics for the specified segment ID. Segments are used for network segmentation within the VeloCloud SD-WAN overlay. |

##	Example usage
```
example_com:velocli> debug --metric_table_dump
[
  {
    "LogicalID": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8",
    "NextHop": [
      {
        "Metric": 81,
      }
    ]
  }
]
```

##	Field descriptions
The output is in JSON format, representing an array of objects. Each object corresponds to a destination logical ID and its associated next-hop metrics.

| Field          | Description                                                                                                                                                              |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LogicalID`    | The unique identifier of the destination peer (e.g., another VeloCloud Edge, Hub, Gateway, or Non-VeloCloud Site) for which transit metrics are being reported.          |
| `NextHop`      | An array of objects. Each object within this array details a specific path or next hop available to reach the destination specified by `LogicalID`, along with its routing metric. |
| `NextHop.Metric` | The calculated cost or preference value for using this particular next hop to reach the destination. This metric is a key input for Overlay Flow Control (OFC) in determining the best path for traffic. Lower values typically indicate a more preferred path. |