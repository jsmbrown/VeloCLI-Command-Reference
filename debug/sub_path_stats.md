#	--sub_path_stats [all | peer-id]

##	Description
This command displays current statistics for sub-paths. Sub-paths are individual connections established over a physical interface to a peer (VeloCloud Gateway or another VeloCloud Edge) for different Classes of Service (CoS). These statistics provide insights into the performance characteristics of each sub-path, including latency, jitter, and loss.

##  Arguments (optional)
| Argument | Description |
|---|---|
| all | Displays sub-path statistics for all peers. This is the default behavior if no argument is specified. |
| peer-id | Displays sub-path statistics only for the specified peer. The peer-id is the logical ID and the friendly name can be retrieved for reference using the ["debug --user_peer_dump"]. |

##  Example usage
```
example_com:velocli> debug --sub_path_stats
Interface   COS ID    PeerName   PublicIpAddr     PeerIpAddr    Version  Path State  RxState  TxState  AvgLatencyRx  AvgLatencyTx  RxJitter  TxJitter  lossRx  lossTx  Precedence  COS Name
GE1              0  vcg44-dfw1  40.122.238.58  216.221.31.44  331634163      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0       LOOSE  Priority
GE1              1  vcg44-dfw1  40.122.238.58  216.221.31.44  331634163      ACTIVE   STABLE   STABLE             3             9       0.0       0.0    0.62     0.0       LOOSE      Bulk
GE1              0  vcg88-ord1  40.122.238.58  216.221.27.88  346328229      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0       LOOSE  Priority
GE1              1  vcg88-ord1  40.122.238.58  216.221.27.88  346328229      ACTIVE   STABLE   STABLE             6             6       0.0       0.0     0.0     0.0       LOOSE      Bulk
```

##  Field descriptions
| Column | Description |
|---|---|
| Interface | The local physical interface on the VeloCloud Edge used for this sub-path (e.g., GE1, GE2). |
| COS ID | The Class of Service Identifier. This numeric ID maps to a specific traffic priority queue. |
| PeerName | The friendly name of the remote VeloCloud peer (Gateway or Edge) to which this sub-path is established. |
| PublicIpAddr | The public IP address of the local VeloCloud Edge interface used for this sub-path. |
| PeerIpAddr | The public IP address of the remote VeloCloud peer. |
| Version | An internal identifier of the WAN config version number associated with the path or peer connection. |
| Path State | The current operational state of the sub-path (e.g., ACTIVE, DEGRADED, DOWN). |
| RxState | The receive state of the sub-path, indicating the stability and health of incoming traffic (e.g., STABLE). |
| TxState | The transmit state of the sub-path, indicating the stability and health of outgoing traffic (e.g., STABLE). |
| AvgLatencyRx | Average latency in milliseconds for received packets on this sub-path. |
| AvgLatencyTx | Average latency in milliseconds for transmitted packets on this sub-path. |
| RxJitter | Jitter in milliseconds observed on received packets for this sub-path. Jitter is the variation in packet arrival times. |
| TxJitter | Jitter in milliseconds observed on transmitted packets for this sub-path. |
| lossRx | Percentage of packet loss for received packets on this sub-path. |
| lossTx | Percentage of packet loss for transmitted packets on this sub-path. |
| Precedence | The selection precedence for this path.  `LOOSE` indicates that user configured queues are in use.  `STRICT` indicates that Strict IP Precedence (where a sub-path is automatically created for each IP Precedence) is enabled. |
| COS Name | The friendly name corresponding to the COS ID, indicating the traffic type or priority (e.g., Priority, Standard, Bulk). |