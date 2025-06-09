#	--iface_top [<sort_column>]

##	Description
Show interface statistics. This command provides a real-time, sortable view of various metrics associated with the VeloCloud Edge's network interfaces. This is useful for monitoring interface health, traffic rates, and error counts.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<sort_column>` | Specifies the column by which the output should be sorted. If omitted, a default sort order is used. Common sortable columns might include interface name, packets/bytes sent/received, or error counts. (The exact available sort columns would be visible in the command's interactive output or further documentation). |

##  Example usage
```
example_com:velocli> debug --iface_top
```
*(The output for `debug --iface_top` is typically a dynamic, continuously updating table. A static example would not fully represent its behavior. The output generally includes columns for interface name, RX/TX packets, RX/TX bytes, RX/TX errors, drops, etc.)*

##  Field descriptions
| Column | Description |
|---|---|
| Interface | The name of the network interface (e.g., GE1, GE2, SFP1, USB1). |
| RX Packets | Number of packets received on the interface. |
| TX Packets | Number of packets transmitted from the interface. |
| RX Bytes | Number of bytes received on the interface. |
| TX Bytes | Number of bytes transmitted from the interface. |
| RX Errors | Number of receive errors on the interface. |
| TX Errors | Number of transmit errors on the interface. |
| RX Drops | Number of received packets dropped by the interface. |
| TX Drops | Number of transmitted packets dropped by the interface. |
| RX Rate (bps) | Current receive rate in bits per second. |
| TX Rate (bps) | Current transmit rate in bits per second. |
| Link | Link status (e.g., Up, Down). |
| Speed | Negotiated speed of the link (e.g., 100Mbps, 1Gbps). |
| Duplex | Duplex mode (e.g., Full, Half). |
*(Note: The exact columns and their names might vary slightly based on the Edge model and software version. The command itself usually provides an interactive display where you can see the available columns.)*