#	--qos_dump_net

##	Description
Displays a hierarchical view of the network Quality of Service (QoS) configuration and current status on the VeloCloud Edge. This includes information about bandwidth allocation, queue limits, and active status for different traffic classes and interfaces. This command is useful for troubleshooting QoS-related issues and understanding how bandwidth is being prioritized and managed.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --qos_dump_net
CC - Child count                AS - Active status                PQ - Pks queued                WT - QoS Weight                BC - Bandwidth cap                QL - QLimit Bytes


  + Device_BW                      ( CC: 2 , AS: 0 , WT: 2000000000 , BC: 0 kbps, QL: 0 B )
     + Direct                         ( CC: 4 , AS: 0 , WT: 2000000000 , BC: 0 kbps, QL: 0 B )
        + VC_Control                     ( CC: 1 , AS: 0 , WT: 2000000000 , BC: 0 kbps, QL: 0 B )
```

##  Field descriptions
The output displays a hierarchical structure where each level can have the following attributes:

| Attribute | Description |
|---|---|
| CC | **Child count**: The number of subordinate QoS classes or queues under this entry. |
| AS | **Active status**: Indicates if the QoS class is currently active. (e.g., 0 for inactive, 1 for active - specific values may vary). |
| PQ | **Pks queued**: The number of packets currently queued for this QoS class. |
| WT | **QoS Weight**: The weight assigned to this class for bandwidth distribution, influencing its priority relative to other classes. |
| BC | **Bandwidth cap**: The maximum bandwidth (in kbps) allocated to this QoS class. A value of 0 kbps might indicate no specific cap or that it inherits from a parent. |
| QL | **QLimit Bytes**: The maximum queue size in bytes for this QoS class. |
| Device_BW | Represents the total bandwidth capacity and QoS settings for the device. |
| Direct | Typically refers to traffic that is directly handled by an interface, often further categorized. |
| VC_Control | Refers to VeloCloud control plane traffic, which is critical for SD-WAN operations. |