#	--path_stats

##	Description

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --path_stats
Interface   VLAN  prio8021P      PeerName                           PublicIpAddr           PeerIpAddr  TunnelingMode     Version  Path State  RxState  TxState  AvgLatencyRx  AvgLatencyTx  RxJitter  TxJitter  lossRx  lossTx  MeasuredRateRx  MeasuredRateTx  dynamicBwRx  dynamicBwTx  RemoteRx  HeartbeatIntervalMs   MTU  Dynamic  Dir  Overhead  DynAbort  LocalGateway
GE5         NONE       NONE    vcg88-ord1                          75.231.53.240        216.221.27.88        DEFAULT  3728705529      ACTIVE   STABLE   STABLE            11            22       2.5       1.0     0.0     0.0          185455           21342       185455        21342     21342                  100  1408       No  OUT         0         1             1
GE6         NONE       NONE    vcg88-ord1  2602:4b:a8c4:9d00:a2ad:9957:8555:890b  2605:a7c0:1:301::88        DEFAULT  2488699796      ACTIVE   STABLE   STABLE            14            13       0.0       0.0     0.0     0.0           38952           19009        38952        19009     19009                  100  1408       No  OUT         0         1             1
GE5         NONE       NONE     AzurevWAN                          75.231.53.240        20.46.246.159        DEFAULT  3805857946      ACTIVE   STABLE   STABLE            18            18       1.5       9.0     0.0     0.0          185455           21342      1509400        21342   3621845                  500  1408       No  OUT         0         1             0
GE6         NONE       NONE     AzurevWAN                         75.168.196.157        20.46.246.159        DEFAULT  2473060710      ACTIVE   STABLE   STABLE            16            15       0.0       0.0     0.0     0.0           38952           19009      1509400        19009   3621845                  100  1408       No  OUT         0         1             0
GE5         NONE       NONE    vcg44-dfw1                          75.231.53.240        216.221.31.44        DEFAULT   420843191      ACTIVE   STABLE   STABLE            20            31       1.5       6.0     0.0     0.0          185455           21342       185455        21342     21342                  500  1408       No  OUT         0         1             0
GE6         NONE       NONE    vcg44-dfw1  2602:4b:a8c4:9d00:a2ad:9957:8555:890b  2605:a7c0:3:301::44        DEFAULT  2493654468      ACTIVE   STABLE   STABLE            22            21       0.0       0.0     0.0     0.0           38952           19009        38952        19009     19009                  500  1408       No  OUT         0         1             0
GE5         NONE       NONE  ARS-Branch-1                          75.231.53.240        40.122.238.58        DEFAULT  3245973656      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0          185455           21342      1182716        21342   2194236                  100  1408      Yes   IN         0         1             0
GE6         NONE       NONE  ARS-Branch-1                         75.168.196.157        40.122.238.58        DEFAULT  3245972410      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0           38952           19009      1182716        19009   2194236                  100  1408      Yes   IN         0         1             0

```

##  Field descriptions
| Column | Description |
|---|---|
| Interface |  |
| VLAN |  |
| prio8021P |  |
| PeerName |  |
| PublicIpAddr |  |
| PeerIpAddr |  |
| TunnelingMode |  |
| Version |  |
| Path State |  |
| RxState |  |
| TxState |  |
| AvgLatencyRx |  |
| AvgLatencyTx |  |
| RxJitter |  |
| TxJitter |  |
| lossRx |  |
| lossTx |  |
| MeasuredRateRx |  |
| MeasuredRateTx |  |
| dynamicBwRx |  |
| dynamicBwTx |  |
| RemoteRx |  |
| HeartbeatIntervalMs |  |
| MTU |  |
| Dynamic |  |
| Dir |  |
| Overhead |  |
| DynAbort |  |
| LocalGateway |  |
