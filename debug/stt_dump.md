#	--stt_dump [all | <transit_log_id>]

##	Description
This command dumps Secure Tunnel Table (STT) entries. STT entries provide information about the state and characteristics of tunnels established or monitored by the VeloCloud Edge. This can be useful for diagnosing connectivity issues or understanding tunnel behavior within the SD-WAN fabric.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays all entries in the Secure Tunnel Table. This is often the default behavior if no argument is specified. |
| `<transit_log_id>` | Filters the output to display STT entries associated with a specific transit log identifier. This allows for targeted troubleshooting of particular paths or tunnels. |

##  Example usage
```
example_com:velocli> debug --stt_dump
Entr_ID   Transit_ID  Node_ID  Cluster  Profile_ID  Reachable  Metric  Uturn  ToC  ToU

```
*(Note: The example output above shows only the headers. Actual output will contain rows of data corresponding to these headers.)*

##  Field descriptions
| Column | Description |
|---|---|
| `Entr_ID` | Entry Identifier: A unique ID for the STT entry. |
| `Transit_ID` | Transit Identifier: An identifier for the transit path or tunnel associated with this entry. This can correlate with the `<transit_log_id>` argument. |
| `Node_ID` | Node Identifier: The identifier of the remote node (e.g., another Edge, Gateway) involved in the tunnel. |
| `Cluster` | Cluster Identifier: If the remote node is part of a cluster, this field indicates the cluster ID. |
| `Profile_ID` | Profile Identifier: The ID of the configuration profile applied to this tunnel or path. |
| `Reachable` | Reachability Status: Indicates whether the remote endpoint of the tunnel is currently reachable (e.g., True/False, 1/0). |
| `Metric` | Path Metric: A numerical value representing the quality or cost of the path, used in path selection algorithms. |
| `Uturn` | U-turn Traffic: Indicates if U-turn traffic (traffic entering and exiting the Edge via the same logical path or interface group, but destined for a different remote site through the overlay) is relevant or configured for this path. |
| `ToC` | Time of Creation: Timestamp indicating when this STT entry was created. |
| `ToU` | Time of Update: Timestamp indicating the last time this STT entry was updated. |