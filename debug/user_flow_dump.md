#	--user_flow_dump [[all | seg-id] [all | src-ip] [all | src-port] [all | dest-ip] [all | dest-port] [max flows to display] [all | v4 | v6]]

##	Description
Displays the current user flow table entries on the VeloCloud Edge. This command provides a snapshot of active traffic flows, including source and destination IP addresses, ports, protocol, application identification, and timing information. This is useful for troubleshooting connectivity and application performance issues.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` (default) or `seg-id` | Filters flows by a specific segment ID. If `all` or no argument is provided, flows from all segments are shown. |
| `all` (default) or `src-ip` | Filters flows by a specific source IP address. If `all` or no argument is provided, flows from all source IPs are shown. |
| `all` (default) or `src-port` | Filters flows by a specific source port. If `all` or no argument is provided, flows from all source ports are shown. |
| `all` (default) or `dest-ip` | Filters flows by a specific destination IP address. If `all` or no argument is provided, flows to all destination IPs are shown. |
| `all` (default) or `dest-port` | Filters flows by a specific destination port. If `all` or no argument is provided, flows to all destination ports are shown. |
| `max flows to display` | Specifies the maximum number of flow entries to display. If not specified, a default limit is applied. |
| `all` (default), `v4`, or `v6` | Filters flows by IP version (IPv4 or IPv6). If `all` or no argument is provided, flows for both versions are shown. |

##  Example usage
```
example_com:velocli> debug --user_flow_dump
SRC_IP                DEST_IP  SRC_PORT  DEST_PORT  PROTO  DSCP                            APP  IDLE_TIME       AGE  TCP_RTT_MS
1.2.3.4         170.85.14.130     41984       7000    TCP     0    HyperText Transfer Protocol     24.883    24.943        0 ms
1.2.3.4         170.85.14.130     38392       7000    TCP     0    HyperText Transfer Protocol     12.668    12.727        0 ms
1.2.3.4         170.85.14.130     41980       7000    TCP     0    HyperText Transfer Protocol     28.954    29.013        0 ms
1.2.3.4         170.85.14.130     55964       7000    TCP     0    HyperText Transfer Protocol     41.170    41.229        0 ms
1.2.3.4         170.85.14.130     60520       7000    TCP     0    HyperText Transfer Protocol   1:34.110  1:34.177        0 ms
```

##  Field descriptions
| Column | Description |
|---|---|
| SRC_IP | Source IP address of the flow. |
| DEST_IP | Destination IP address of the flow. |
| SRC_PORT | Source port number of the flow. |
| DEST_PORT | Destination port number of the flow. |
| PROTO | Protocol used by the flow (e.g., TCP, UDP, ICMP). |
| DSCP | Differentiated Services Code Point value, indicating the Quality of Service (QoS) marking of the flow. |
| APP | Application identified for the flow (e.g., HyperText Transfer Protocol). |
| IDLE_TIME | Time in seconds (or minutes:seconds.milliseconds) since the last packet was seen for this flow. |
| AGE | Total time in seconds (or minutes:seconds.milliseconds) the flow has been active. |
| TCP_RTT_MS | For TCP flows, the measured Round Trip Time in milliseconds. |