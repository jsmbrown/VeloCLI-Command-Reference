#	--pim_neighbor

##	Description
Dumps a summary of Protocol Independent Multicast (PIM) neighbors known to the VeloCloud Edge. PIM is used for routing multicast traffic within network segments and potentially across the SD-WAN overlay.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --pim_neighbor
SegId   PimInterface  PeerName

show ip pim neighbor
====================
 Interface  Neighbor  Uptime  Holdtime  DR Pri
```

##  Field descriptions
The output displays PIM neighbor information, potentially in two sections:

**PIM Neighbor Summary (VeloCloud Specific):**
| Column | Description |
|---|---|
| SegId | The Segment ID associated with the PIM interface. This indicates which VeloCloud network segment the PIM adjacency belongs to. |
| PimInterface | The name of the local VeloCloud Edge interface on which PIM is enabled and has formed an adjacency. |
| PeerName | The hostname or identifier of the PIM peer. This could be another VeloCloud Edge or a third-party multicast router. |

**Detailed PIM Neighbor Information (Standard PIM Output):**
This section typically reflects the output of a standard `show ip pim neighbor` command.
| Column | Description |
|---|---|
| Interface | The network interface on which the PIM neighbor relationship is established. |
| Neighbor | The IP address of the PIM neighbor. |
| Uptime | The duration for which the PIM neighbor adjacency has been active (e.g., "00:05:12" for 5 minutes and 12 seconds). |
| Holdtime | The time remaining (in seconds) before the PIM neighbor adjacency will expire if no further PIM hello messages are received from this neighbor. |
| DR Pri | The Designated Router (DR) priority of the neighbor on this interface. The router with the highest DR priority (or highest IP address in case of a tie) becomes the DR for the LAN segment, responsible for registering and forwarding multicast traffic. |