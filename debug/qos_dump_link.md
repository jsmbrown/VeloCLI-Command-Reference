#	--qos_dump_link

##	Description
The `debug --qos_dump_link` command displays a detailed snapshot of the current Quality of Service (QoS) configuration and operational status for network links on the VeloCloud Edge. This output helps in understanding how QoS policies are applied, including the hierarchical structure of QoS classes, bandwidth allocation parameters (weights and caps), and real-time packet queuing statistics. This information is crucial for troubleshooting traffic prioritization and ensuring the desired Quality of Experience (QoE) for various applications.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --qos_dump_link
CC - Child count                AS - Active status                PQ - Pks queued                WT - QoS Weight                BC - Bandwidth cap                QL - QLimit Bytes


  + Root                           ( CC: 1 , AS: 0 , WT: 2000000000 , BC: 0 kbps, QL: 0 B )
     + eth0                           ( CC: 23 , AS: 0 , WT: 2000000000 , BC: 0 kbps, QL: 0 B )
        + Flow - 0/0          ( AS: 0 , PQ: 0 , QL: 0B )
```

##  Field descriptions
The output displays a legend for abbreviations used:
*   **CC**: Child count
*   **AS**: Active status
*   **PQ**: Packets queued
*   **WT**: QoS Weight
*   **BC**: Bandwidth cap
*   **QL**: QLimit Bytes

The output is structured hierarchically:

| Item                       | Description                                                                                                |
|----------------------------|------------------------------------------------------------------------------------------------------------|
| `+ Root`                   | The top-level entity in the QoS hierarchy for a link.                                                      |
| `  + <interface_name>`     | Represents a network interface (e.g., `eth0`) on the Edge, showing its QoS configuration and child elements. |
| `    + Flow - X/Y`         | Represents a specific traffic flow, often corresponding to a defined QoS class or queue.                     |
| `( CC: value, ... )`       | Attributes for each entity in the hierarchy, as defined by the legend above.                               |

Detailed attribute descriptions:
| Attribute | Description                                                                                                |
|-----------|------------------------------------------------------------------------------------------------------------|
| `CC`      | **Child Count**: The number of subordinate QoS classes or queues under the current entity.                   |
| `AS`      | **Active Status**: Indicates the operational status of the QoS entity (e.g., 0 might mean inactive or no active traffic matching this specific queue at the moment of the dump). |
| `PQ`      | **Packets Queued**: The current number of packets waiting in the queue for this QoS entity.                  |
| `WT`      | **QoS Weight**: A relative value used by the scheduler to distribute bandwidth among queues. Higher weights typically receive a larger share of available bandwidth when contention occurs. |
| `BC`      | **Bandwidth Cap**: The maximum bandwidth, in kilobits per second (kbps), that this QoS entity is allowed to use. A value of `0 kbps` might indicate no specific cap is set at this level, or it inherits from a parent. |
| `QL`      | **QLimit Bytes**: The maximum size of the queue in bytes. Packets may be dropped if this limit is exceeded.   |