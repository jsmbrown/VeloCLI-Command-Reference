#	--psummary

##	Description
Displays a summary of the current state of all paths (tunnels) established by the VeloCloud Edge. This includes paths to other VeloCloud Edges and VeloCloud Gateways, categorized by their stability and operational status.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
```
example_com:velocli> debug --psummary
PEER TYPE   PEER_COUNT  STABLE  UNSTABLE  INITIAL  DEAD  UNUSABLE  QUIET  MEASURING  BW_UNMEASURABLE  WAITING_FOR_LINK_BW  TOTAL_PATHS  TOTAL_DYNAMIC  TOTAL_STATIC
EDGE                 1       1         0        0     0         0      0          0                0                    0            1              0             1
GATEWAY              3       2         0        1     0         0      0          0                0                    0            3              0             3

```
##  Field descriptions
| Column | Description |
|---|---|
| PEER TYPE | The type of remote peer the path connects to (e.g., EDGE, GATEWAY). |
| PEER_COUNT | The number of peers of the specified type. |
| STABLE | The number of paths to this peer type that are currently stable and operational. |
| UNSTABLE | The number of paths to this peer type that are currently experiencing issues (e.g., high loss, latency, jitter) affecting their stability. |
| INITIAL | The number of paths to this peer type that are in the process of being established or are newly formed. |
| DEAD | The number of paths to this peer type that are no longer active or have failed. |
| UNUSABLE | The number of paths to this peer type that are currently deemed unusable for traffic. |
| QUIET | The number of paths to this peer type that are in a quiet state due to inactivity. |
| MEASURING | The number of paths to this peer type for which performance characteristics (like bandwidth) are actively being measured. |
| BW_UNMEASURABLE | The number of paths to this peer type where bandwidth measurement is not possible or has failed. |
| WAITING_FOR_LINK_BW | The number of paths to this peer type that are waiting for underlying link bandwidth information before becoming fully operational or measured. |
| TOTAL_PATHS | The total number of paths (both dynamic and static) to this peer type. |
| TOTAL_DYNAMIC | The total number of dynamically established paths (e.g., DE2E) to this peer type. |
| TOTAL_STATIC | The total number of statically configured paths (e.g., to Hub Edges or Gateways) to this peer type. |