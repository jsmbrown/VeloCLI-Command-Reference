#	--edge_peers

##	Description
Dumps all peer subnets and their gateway associations. This command provides a list of VeloCloud Edges and Gateways that are peers to the current edge, along with details about their IP address family and segment ID.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --edge_peers
{
  "edge_peers": [
    {
      "family": "IPv4",
      "peer_id": "88616e5e-e59b-406e-9c1e-39cd29cc9385",
      "segment_id": 0
      "subnet_count": 7,
      "type": 1
    }
  ]
}
```

##  Field descriptions
| Field         | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `edge_peers`  | An array containing objects, where each object represents a peer VeloCloud Edge. |
| `family`      | The IP address family used for communication with the peer (e.g., "IPv4", "IPv6"). |
| `peer_id`     | The unique logical identifier of the peer VeloCloud Edge.                     |
| `segment_id`  | The network segment ID to which this peer information pertains.             |
| `subnet_count`  | Quantity of subnets advertised by the peer.  |