#	--sor_dump [all | <node_id>]

##	Description
The `debug --sor_dump` command is used to display entries from the Source of Record (SoR) table. The SoR maintains state information about various nodes and paths within the VeloCloud SD-WAN fabric. This information is crucial for routing decisions and understanding the topology from the perspective of the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays all entries in the SoR table. This is the default behavior if no argument is specified. |
| `<node_id>` | Displays SoR entries specifically related to the given Node ID. The Node ID typically refers to another VeloCloud Edge or Gateway. |

##  Example usage
```
example_com:velocli> debug --sor_dump
Entr_ID   Node_ID  Transit  Cluster  Profile_ID  D/R  Reachable  Metric  Uturn  ToC  ToU  Uturn_Transit_Count

example_com:velocli> debug --sor_dump <specific_node_id>
Entr_ID   Node_ID  Transit  Cluster  Profile_ID  D/R  Reachable  Metric  Uturn  ToC  ToU  Uturn_Transit_Count
(Output specific to the node_id would be shown here)
```

##  Field descriptions
| Column | Description |
|---|---|
| Entr_ID | Entry Identifier: A unique ID for this specific SoR entry. |
| Node_ID | Node Identifier: The unique identifier of the VeloCloud peer (Edge or Gateway) to which this entry pertains. |
| Transit | Transit Capability: Indicates if the peer node can act as a transit point for traffic (e.g., a Hub Edge or Gateway). |
| Cluster | Cluster Identifier: If the peer node is part of a cluster (e.g., a high-availability hub cluster), this field may show the cluster ID. |
| Profile_ID | Profile Identifier: The configuration profile ID associated with the peer node. |
| D/R | Direct/Remote: Indicates if the peer is directly connected or reached remotely. (Interpretation may vary based on specific internal logic). |
| Reachable | Reachability Status: A boolean (True/False) or similar indicator showing whether the peer node is currently considered reachable. |
| Metric | Path Metric: A numerical value representing the cost or quality of the path to this node, used in routing decisions. Lower values are generally preferred. |
| Uturn | U-turn Traffic: Indicates properties or policies related to U-turn traffic (traffic that enters and exits the SD-WAN fabric via the same Edge, often relevant for spoke-to-spoke communication via a Hub). |
| ToC | Time of Creation: Timestamp indicating when this SoR entry was created. |
| ToU | Time of Update: Timestamp indicating when this SoR entry was last updated. |
| Uturn_Transit_Count | U-turn Transit Count: A counter related to U-turn traffic transiting through or related to this node/path. |