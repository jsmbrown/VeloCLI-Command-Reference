#	--fdisp_top [core-id|all]

##	Description
Displays real-time statistics for the flow dispatcher on the VeloCloud Edge. This command provides insights into how network traffic flows are being processed by different CPU cores, including CPU utilization, flow counts, packet queuing, and performance metrics for various packet processing actions. This is useful for diagnosing performance bottlenecks or understanding packet handling behavior.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `core-id` | Specifies a particular CPU core ID for which to display statistics. |
| `all` | Displays statistics for all available CPU cores. This is the default if no argument is provided. |

##  Example usage
```
example_com:velocli> debug --fdisp_top
100.00% Core 0: flows=206, stale-flows=0, queued-pkts=0 (max 29490)
   |--- 89.63% Actions
   |       |--- 27.83%              78: send_pkt_mgmt                               min=3211ns      max=8491ns      hits=17/s      drops=0/s     
   |       |--- 25.68%              64: prep_pkt_for_fwd                            min=865ns       max=7247ns      hits=32/s      drops=0/s     
   |       |--- 18.44%              59: check_for_exceptions                        min=693ns       max=3119ns      hits=31/s      drops=0/s     
   |       |--- 10.68%              63: rx_account                                  min=697ns       max=2077ns      hits=32/s      drops=0/s     
```
##  Field descriptions
| Column/Field | Description |
|---|---|
| **Overall Core Statistics (First Line)** | |
| `[percentage]% Core [id]` | Percentage of CPU time this core spends on flow dispatching, and the core ID. |
| `flows` | Current number of active flows being handled by this core. |
| `stale-flows` | Number of flows that are no longer active but have not yet been fully removed by this core. |
| `queued-pkts` | Current number of packets waiting in the queue for processing by this core. |
| `(max [number])` | Maximum number of packets observed in the queue for this core since statistics collection began or was reset. |
| **Action Breakdown (Indented Lines)** | |
| `[percentage]% Actions` | Percentage of the core's flow dispatching time spent executing various packet processing actions. |
| `[percentage]%` | Percentage of the total "Actions" time spent on this specific action. |
| `[id]: [action_name]` | Internal identifier and descriptive name for the specific packet processing action. |
| `min` | Minimum time taken to execute this action, typically in nanoseconds (ns). |
| `max` | Maximum time taken to execute this action, typically in nanoseconds (ns). |
| `hits` | Rate at which this action is being executed, typically in hits per second (/s). |
| `drops` | Rate at which packets are being dropped by this specific action, typically in drops per second (/s). |