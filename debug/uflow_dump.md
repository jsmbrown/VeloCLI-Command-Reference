#	--uflow_dump [all | src-ip] [all | dest-ip] [all | segid]

##	Description
Dumps the current uflow (micro-flow or user flow) table entries on the VeloCloud Edge. This table tracks active network connections, providing details such as source/destination IP addresses, ports, protocol, segment ID, and traffic statistics. It is useful for troubleshooting connectivity and understanding real-time traffic patterns through the Edge.

##	Arguments (optional)
The command accepts up to three positional arguments to filter the uflow entries. If an argument is omitted, it defaults to `all` for that position and any subsequent positions.

| Position | Argument Name (Conceptual) | Allowed Values        | Default | Description                                                                                             |
|----------|----------------------------|-----------------------|---------|---------------------------------------------------------------------------------------------------------|
| 1        | Source IP Filter           | `all` or `<src-ip>`   | `all`   | Filters flows by the source IP address. `<src-ip>` should be a specific IP address (e.g., `192.168.1.10`). |
| 2        | Destination IP Filter      | `all` or `<dest-ip>`  | `all`   | Filters flows by the destination IP address. `<dest-ip>` should be a specific IP address (e.g., `8.8.8.8`). |
| 3        | Segment ID Filter          | `all` or `<segid>`    | `all`   | Filters flows by the segment ID. `<segid>` should be a numerical segment identifier (e.g., `1`, `10`).      |

For example:
*   `debug --uflow_dump 192.168.1.10` is equivalent to `debug --uflow_dump 192.168.1.10 all all`.
*   `debug --uflow_dump 192.168.1.10 8.8.8.8` is equivalent to `debug --uflow_dump 192.168.1.10 8.8.8.8 all`.
*   `debug --uflow_dump all all 1` filters for flows on segment ID 1, regardless of source or destination IP.

##	Example usage
To dump all uflow entries:
```
example_com:velocli> debug --uflow_dump
```

To dump uflow entries for a specific source IP `192.168.10.5`, any destination IP, on segment `1`:
```
example_com:velocli> debug --uflow_dump 192.168.10.5 all 1
```

**(Note: The example output provided in the prompt for this command shows usage help for the `debug.py` script. A typical successful execution of `debug --uflow_dump` would display a table listing the active flow entries. The following is a conceptual representation of such output for `debug --uflow_dump` without filters):**
```
Src IP          Dst IP          Src Port Dst Port Proto  Segment ID  Application ID  State   Packets Bytes   In Interface Out Interface  Flags
192.168.1.10    8.8.8.8         54321    53       UDP    1           53 (DNS)        ACTIVE  10      800     GE1          WAN1           -
10.0.0.5        172.16.0.10     12345    443      TCP    2           443 (HTTPS)     ESTAB   150     150000  LAN2         TUN0           FPA
...
```

##	Field descriptions
The following are common fields found in the uflow dump output. Actual fields and their exact names may vary depending on the VeloCloud Edge software version and configuration.

| Column          | Description                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------|
| `Src IP`        | Source IP address of the flow.                                                                             |
| `Dst IP`        | Destination IP address of the flow.                                                                        |
| `Src Port`      | Source port number (for TCP/UDP protocols).                                                                |
| `Dst Port`      | Destination port number (for TCP/UDP protocols).                                                           |
| `Proto`         | Protocol of the flow (e.g., TCP, UDP, ICMP, or protocol number).                                           |
| `Segment ID`    | The VeloCloud segment ID associated with the flow. Segments are used for network traffic isolation.        |
| `Application ID`| Identifier for the application associated with the flow, often derived from port or deep packet inspection. |
| `State`         | Current state of the flow (e.g., `NEW`, `ACTIVE`, `ESTAB` for TCP, `CLOSED`).                                |
| `Packets`       | Number of packets that have traversed this flow in one direction (e.g., forward path).                     |
| `Bytes`         | Number of bytes that have traversed this flow in one direction (e.g., forward path).                       |
| `In Interface`  | Ingress interface on the Edge where the flow originated or was received.                                   |
| `Out Interface` | Egress interface on the Edge where the flow is being sent. This could be a WAN link, LAN port, or tunnel.   |
| `Flags`         | Various flags indicating properties, state, or treatment of the flow (e.g., offloaded, prioritized, NATed). |