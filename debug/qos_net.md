#	--qos_net [ <peer_id> | gateway ] [ all | <segid> ] [ stats | clear_drops ]

##	Description
Executed on a VeloCloud Edge, this command provides a debug interface for network Quality of Service (QoS) functionalities. It allows for the inspection of QoS statistics and the management of packet drop counters related to traffic handling over the SD-WAN overlay paths. The command's scope can be narrowed to specific peer Edges, VeloCloud Gateways, and particular network segments, aiding in the monitoring and troubleshooting of Quality of Experience (QoE) by providing insights into traffic prioritization and management.

##  Arguments (optional)
The arguments are positional. If an earlier argument is not specified, subsequent arguments cannot be specified.

| Argument        | Description                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (none)          | If no arguments are provided, the command typically displays default QoS statistics, potentially for all targets (peer Edges and Gateways) across all accessible network segments.                       |
| `<peer_id>`     | As the first argument: Specifies a VeloCloud Edge peer by its unique identifier. The command's output will then be scoped to QoS information related to this specific peer.                               |
| `gateway`       | As the first argument: Specifies that the command pertains to QoS information related to a VeloCloud Gateway connected to this Edge.                                                                      |
| `all`           | As the second argument (requires `<peer_id>` or `gateway` to be specified as the first argument): Indicates that the command should apply to all network segments relevant to the specified target.        |
| `<segid>`       | As the second argument (requires `<peer_id>` or `gateway` to be specified as the first argument): Specifies a particular network segment by its ID. The command's scope for the chosen target will be limited to this segment. |
| `stats`         | As the third argument (requires a target and segment specifier as the first and second arguments): Instructs the command to display QoS statistics for the specified scope. This may be the default action if this argument is omitted but preceding arguments are present. |
| `clear_drops`   | As the third argument (requires a target and segment specifier as the first and second arguments): Instructs the command to clear packet drop counters associated with QoS mechanisms for the specified target and segment. |

##  Example usage
```
example_com:velocli> debug --qos_net
```
(The command above is run without arguments, which would typically display default QoS statistics.)

##  Field descriptions
| Column | Description |
|---|---|
|   | (Specific output fields depend on the arguments used. No example output was provided for this command.) |