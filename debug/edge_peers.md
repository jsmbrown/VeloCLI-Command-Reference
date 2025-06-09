#	--edge_peers

##	Description
This command displays a list of all peer VeloCloud Edges known to the local Edge. For each peer, it shows associated subnets and the VeloCloud Gateway through which the peer is reached. This information is crucial for understanding the dynamic tunnel (DE2E) and static tunnel connectivity within the SD-WAN overlay.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##  Example usage
```
example_com:velocli> debug --edge_peers
{
  "edge_peers": []
}
```
*Note: The example above shows an empty list, indicating no active peer connections or that the command was run on an Edge with no established peer relationships at that moment. In a populated environment, the array would contain objects detailing each peer.*

##  Field descriptions
| Field | Description |
|---|---|
| edge_peers | A JSON array where each element represents a peer Edge. The specific details within each peer object (not shown in the empty example) would typically include information such as the peer Edge's ID, its advertised subnets, and the Gateway facilitating the connection. |