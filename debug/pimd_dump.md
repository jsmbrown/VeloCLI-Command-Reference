#	--pimd_dump

##	Description
Displays the current status and operational information of the Protocol Independent Multicast daemon (pimd) running on the VeloCloud Edge. This includes details about PIM interfaces, neighbors, and multicast routing state. PIM is used to efficiently route multicast traffic within the network.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --pimd_dump
```
*(Note: The output of this command can be extensive and will vary based on the PIM configuration and current multicast traffic. It typically includes sections for PIM interface status, neighbor adjacencies, multicast group information, and Rendezvous Point (RP) status if applicable.)*

##  Field descriptions
The output of `debug --pimd_dump` provides a comprehensive overview of the PIM daemon's state. While the exact format can vary, common sections and fields include:

| Category/Section        | Field/Information                      | Description                                                                                                |
|-------------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------|
| **PIM Interface Table** | Interface Name                         | The network interface on which PIM is active.                                                              |
|                         | Mode                                   | PIM mode (e.g., Sparse, Dense, Sparse-Dense).                                                              |
|                         | State                                  | Current operational state of PIM on the interface (e.g., DR - Designated Router, Non-DR).                    |
|                         | Hello Interval/Holdtime                | Timers used for PIM neighbor discovery and maintenance.                                                    |
|                         | DR Priority                            | Priority value used in Designated Router election.                                                         |
| **PIM Neighbor Table**  | Neighbor Address                       | IP address of the PIM neighbor.                                                                            |
|                         | Uptime                                 | Duration for which the PIM adjacency with the neighbor has been active.                                    |
|                         | Mode                                   | PIM mode supported by the neighbor.                                                                        |
|                         | Options                                | PIM options exchanged with the neighbor.                                                                   |
| **Multicast Routing Information Base (MRIB) / Forwarding Table** | Group Address (G)                      | The destination multicast group address.                                                                   |
|                         | Source Address (S)                     | The source IP address of the multicast traffic; can be `*` for any source (in (*,G) entries).              |
|                         | RPF Interface                          | Reverse Path Forwarding interface; the interface leading back to the source or RP.                         |
|                         | RPF Neighbor                           | The PIM neighbor on the RPF interface.                                                                     |
|                         | Outgoing Interface List (OIL)          | List of interfaces on which multicast traffic for this (S,G) or (*,G) entry will be forwarded.             |
|                         | Timers                                 | Various timers associated with the multicast route entry (e.g., prune timers, join timers).                |
| **RP (Rendezvous Point) Information** (if PIM-SM is active) | RP Address                             | IP address of the active Rendezvous Point(s).                                                              |
|                         | RP Type                                | How the RP was learned (e.g., Static, BSR - Bootstrap Router).                                             |
|                         | Group Range                            | Multicast group range for which this RP is responsible.                                                    |
| **General Status**      | Version                                | PIM protocol version being used.                                                                           |
|                         | Uptime                                 | How long the pimd process has been running.                                                                |
|                         | Counters                               | Various statistics like number of PIM messages sent/received, number of RPF failures, etc.                 |

*The specific fields and their layout depend on the implementation of the `pimd` on the VeloCloud Edge. The output is generally intended for advanced troubleshooting of multicast routing issues.*