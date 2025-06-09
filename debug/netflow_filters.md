#	--netflow_filters [<collector_id>]

##	Description
Displays the configured Netflow filters. If a specific `collector_id` is provided, the output will be limited to the filters associated with that collector. Otherwise, filters for all collectors may be displayed. Netflow is a network protocol developed by Cisco for collecting IP traffic information and monitoring network flow. VeloCloud Edges can be configured to export Netflow records to one or more external collectors for traffic analysis.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<collector_id>` | The ID of a specific Netflow collector. If provided, the command will only display filters associated with this collector. If omitted, filters for all configured collectors might be displayed. Collector IDs can typically be found using the `debug --netflow_collectors` command. |

##  Example usage
```
example_com:velocli> debug --netflow_filters
```
*(Note: The output for this command will list the configured Netflow filters. Specific output format may vary.)*

##  Field descriptions
The output will typically list the criteria that define which network flows are captured and exported by Netflow. This may include:
| Field | Description |
|---|---|
| Filter ID | A unique identifier for the filter rule. |
| Source IP/Prefix | The source IP address or network prefix to match. |
| Destination IP/Prefix | The destination IP address or network prefix to match. |
| Protocol | The IP protocol to match (e.g., TCP, UDP, ICMP). |
| Source Port | The source port number for TCP/UDP traffic. |
| Destination Port | The destination port number for TCP/UDP traffic. |
| DSCP Value | Differentiated Services Code Point value to match. |
| Action | The action to take for matching flows (e.g., include, exclude). |
| Associated Collector ID | The ID of the Netflow collector to which this filter applies. |
*(The exact fields and their names might vary based on the specific software version and configuration.)*