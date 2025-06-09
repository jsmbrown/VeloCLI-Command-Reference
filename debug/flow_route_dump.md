# `debug --flow_route_dump <scope> <destination> <segment> [option]`

## Description
The `debug --flow_route_dump` command displays entries from the VeloCloud Edge's flow_route table. This table is crucial for understanding how active traffic flows are being routed through the SD-WAN overlay, including path selection and policy enforcement. It helps in troubleshooting connectivity and performance issues for specific traffic patterns by showing detailed routing information for individual flows or sets of flows based on specified criteria.

## Arguments

This command requires three mandatory arguments and accepts one optional argument.

| Argument | Description | Accepted Values |
|---|---|---|
| `<scope>` | Specifies the primary filter for the flow dump. This determines the context of the flows to be displayed. | <ul><li>`local`: Displays flows that are locally originated or terminated at the Edge.</li><li>`<logical_id_value>`: A specific logical identifier (e.g., for a remote peer, service, or interface). The command will display flows associated with this logical ID.</li><li>`all`: Displays flows without filtering by a specific scope or logical ID.</li></ul> |
| `<destination>` | Filters the flows based on their destination IP address. | <ul><li>`all`: Displays flows destined for any IP address.</li><li>`<destination_ip>`: A specific IPv4 or IPv6 destination address (e.g., `192.168.1.100`, `2001:db8::1`).</li></ul> |
| `<segment>` | Filters the flows based on their segment ID. Segments are used in VeloCloud SD-WAN for network segmentation. | <ul><li>`all`: Displays flows across all segments.</li><li>`<segment_id_value>`: A specific segment ID (e.g., `0`, `1`, `100`).</li></ul> |
| `[option]` (optional) | Provides additional filtering or display options for the selected flows. | <ul><li>`flowIdx`: May display additional flow index information or filter by a specific flow index. The exact behavior (e.g., if it expects a subsequent index value) might depend on the specific implementation details not fully captured by the syntax.</li><li>`noroute`: Displays only those flow entries that currently have no valid route in the SD-WAN fabric. This is useful for identifying traffic that is failing due to routing issues.</li></ul> |

## Example Usage

### Dumping all flow_route entries for a specific destination IP across all scopes and segments:
```
example_com:velocli> debug --flow_route_dump all 8.8.8.8 all
```
*(Output would be a table of flow_route entries matching the criteria. Format not provided in example.)*

### Dumping local flow_route entries for a specific destination IP in segment 0, showing only those with no route:
```
example_com:velocli> debug --flow_route_dump local 10.0.0.5 0 noroute
```
*(Output would be a table of local flow_route entries for 10.0.0.5 in segment 0 that are in a 'noroute' state.)*

### Example of insufficient arguments:
The command requires a minimum of three arguments as shown below.
```
example_com:velocli> debug --flow_route_dump
Insufficient Arguments provided. Minimum number of argument is 3.
                  usage: --flow_dump [local | logical-id | all] [all | dest-ip] [all | segid]
```
*Note: The error message refers to `--flow_dump` which might be an internal alias or related command, but the argument structure shown applies to `debug --flow_route_dump`.*

## Field Descriptions
The output of `debug --flow_route_dump` is typically a table where each row represents a flow_route entry. While the exact column names can vary, common fields include:

| Column (Potential) | Description |
|---|---|
| Source IP | The source IP address of the flow. |
| Destination IP | The destination IP address of the flow. |
| Protocol | The IP protocol of the flow (e.g., TCP, UDP, ICMP). |
| Source Port | The source port for TCP or UDP flows. |
| Destination Port | The destination port for TCP or UDP flows. |
| Segment ID | The segment to which the flow belongs. |
| Ingress Interface | The interface on which the flow arrived at the Edge. |
| Egress Interface / Path | Information about the outgoing path chosen for the flow (e.g., tunnel ID, next-hop gateway, specific WAN link). |
| Policy Information | Details of any business policies or routing policies applied to the flow. |
| Flow Index | A unique identifier for the flow within the system. |
| State / Flags | Status flags or state information related to the flow's routing (e.g., `Routed`, `NoRoute`, `PolicyDrop`). |
| QoE Metrics | Potentially, Quality of Experience metrics if the flow is being monitored. |

*The specific fields and their exact names will be visible in the header row of the command's output.*