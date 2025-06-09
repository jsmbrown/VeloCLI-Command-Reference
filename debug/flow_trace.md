#	--flow_trace [v4 | v6] [segment_id=<int>] [protocol=<int>] [src_port=<int>] [dst_port=<int>] [src_ip=<str>] [dst_ip=<str>] [count=<int>] [timeout=<int>]

##	Description
Enables or disables tracing of user data flows through the VeloCloud Edge. When called with specific filter arguments, it initiates a flow trace based on those criteria, allowing for detailed inspection of packet paths and forwarding decisions. When called without any arguments, it typically disables any active flow trace or reports the current disabled status of the feature. This command is useful for troubleshooting connectivity and routing issues for specific traffic patterns.

##	Arguments (optional)
All arguments are optional. If no arguments are provided, flow tracing is disabled (or its disabled status is reported), as shown in the example. If one or more arguments are provided, they act as filters to define the specific flows to be traced. If neither `v4` nor `v6` is specified, the trace may apply to both IPv4 and IPv6 traffic matching other filters, or it may default to IPv4. The IP version specified in `src_ip` or `dst_ip` will implicitly define the IP version for the trace if `v4` or `v6` is not explicitly set.

| Argument | Description |
|---|---|
| `v4` | Trace only IPv4 flows. Mutually exclusive with `v6`. |
| `v6` | Trace only IPv6 flows. Mutually exclusive with `v4`. |
| `segment_id=<int>` | Filter flows belonging to the specified VeloCloud segment ID. Example: `segment_id=1`. |
| `protocol=<int>` | Filter flows by IP protocol number (e.g., 6 for TCP, 17 for UDP, 1 for ICMP). Example: `protocol=6`. |
| `src_port=<int>` | Filter flows by source Layer 4 port number. Typically used with `protocol=6` (TCP) or `protocol=17` (UDP). Example: `src_port=12345`. |
| `dst_port=<int>` | Filter flows by destination Layer 4 port number. Typically used with `protocol=6` (TCP) or `protocol=17` (UDP). Example: `dst_port=80`. |
| `src_ip=<str>` | Filter flows by source IP address (IPv4 or IPv6). Example: `src_ip=192.168.1.10` or `src_ip=2001:db8::1`. |
| `dst_ip=<str>` | Filter flows by destination IP address (IPv4 or IPv6). Example: `dst_ip=8.8.8.8` or `dst_ip=2001:db8::2`. |
| `count=<int>` | Specifies the maximum number of packets to capture for flows matching the criteria. Once this count is reached for a matching flow, tracing for that specific flow might stop, or the entire trace operation might cease depending on the implementation. Example: `count=100`. |
| `timeout=<int>` | Specifies the duration (in seconds) for which the flow trace will be active. After this timeout period, tracing stops automatically. Example: `timeout=60`. |

##	Example Usage
The command below, when issued without any arguments, disables any active flow trace or reports that tracing is currently disabled:
```
example_com:velocli> debug --flow_trace
Flow trace disabled
```

To enable flow tracing with specific filters, provide the relevant arguments. For instance, to trace the first 10 TCP packets from source IP 192.168.1.50 to destination IP 8.8.8.8 on destination port 53, for a duration of 120 seconds:
```
example_com:velocli> debug --flow_trace src_ip=192.168.1.50 dst_ip=8.8.8.8 protocol=6 dst_port=53 count=10 timeout=120
```
(Note: The output confirming trace activation or the trace data itself is not shown in this example and may vary. The actual trace data is typically viewed through other means, such as system logs or specific `show` commands.)

##	Field Descriptions
The output `Flow trace disabled` indicates the state of the flow tracing feature when queried without arguments or after being explicitly disabled.

When flow tracing is enabled using filter arguments, the command might output a confirmation message (not shown in the example). The actual captured flow data is not directly displayed by this command but is typically directed to system logs, a separate buffer, or made available through other diagnostic commands. The content of the captured data would generally include details such as:
*   Timestamps
*   Source and Destination IP addresses
*   Source and Destination L4 ports (if applicable)
*   IP Protocol
*   Ingress and Egress interfaces
*   Packet path information within the SD-WAN overlay (e.g., selected tunnel/path)
*   Forwarding decisions and applied policies

The specific format and method for accessing the detailed trace output can vary.