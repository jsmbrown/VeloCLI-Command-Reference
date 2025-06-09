#	--psummary

##	Description
Displays a summary of the current state of all paths (tunnels) established by the VeloCloud Edge. This includes paths to other Edges and to VeloCloud Gateways. The summary categorizes paths by their stability and operational status.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --psummary
PEER TYPE   PEER_COUNT  STABLE  UNSTABLE  INITIAL  DEAD  UNUSABLE  QUIET  MEASURING  BW_UNMEASURABLE  WAITING_FOR_LINK_BW  TOTAL_PATHS  TOTAL_DYNAMIC  TOTAL_STATIC
EDGE                 0       0         0        0     0         0      0          0                0                    0            0              0             0
GATEWAY              0       0         0        0     0         0      0          0                0                    0            0              0             0

```
##  Field descriptions
| Column | Description |
|---|---|
| PEER TYPE | The type of peer the path is established with (EDGE or GATEWAY). |
| PEER_COUNT | The number of unique peers of this type. |
| STABLE | The number of paths to this peer type that are currently stable and performing within acceptable QoE thresholds. |
| UNSTABLE | The number of paths to this peer type that are currently experiencing issues (e.g., high loss, latency, or jitter) and are considered unstable. |
| INITIAL | The number of paths to this peer type that are in the initial state of establishment. |
| DEAD | The number of paths to this peer type that are no longer active or reachable. |
| UNUSABLE | The number of paths to this peer type that are currently unusable due to underlying link issues or other problems. |
| QUIET | The number of paths to this peer type that are in a quiet state, typically meaning no traffic is being sent, or they are administratively down. |
| MEASURING | The number of paths to this peer type that are currently undergoing performance measurement (e.g., bandwidth testing). |
| BW_UNMEASURABLE | The number of paths to this peer type where bandwidth measurement could not be completed. |
| WAITING_FOR_LINK_BW | The number of paths to this peer type that are waiting for underlying link bandwidth information before becoming fully operational. |
| TOTAL_PATHS | The total number of paths (both dynamic and static) to this peer type. |
| TOTAL_DYNAMIC | The total number of dynamically created paths (e.g., DE2E) to this peer type. |
| TOTAL_STATIC | The total number of statically configured paths (e.g., to Hub Edges or Gateways) to this peer type. |