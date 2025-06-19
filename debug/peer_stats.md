#	--peer_stats `[ <peer_id> | all ] [detailed | all]`

##	Description
Displays statistics for each peer VeloCloud Edge or Gateway. The `detailed` option provides additional path statistics for each tunnel established with the peer. This information is useful for monitoring the health and performance of connections to other SD-WAN nodes in the overlay network.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<peer_id>` | Specifies the logical ID of a particular peer for which to display statistics. |
| `all` (first argument) | Displays statistics for all known peers. This is the default if no peer ID is specified. |
| `detailed` | Includes detailed path statistics for each tunnel associated with the peer(s). |
| `all` (second argument) | Standard output without individual path details.  This is the default if no 2nd argument is provided. |

##  Example usage
```
example_com:velocli> debug --peer_stats
{
  "peer_stats_dump": [
    {
      "path_stats": [],
      "peer_logical_id": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8",
      "peer_name": "vcg44-dfw1"
      "peer_type": "VCE",
      "rx_bytes": 923815640,
      "rx_packets": 1193241,
      "tx_bytes": 171525558,
      "tx_packets": 903406
    }
  ]
}
```

##  Field descriptions
| Field | Description |
|---|---|
| `peer_stats_dump` | An array containing statistics for one or more peers. |
| `path_stats` | An array containing detailed statistics for each individual path (tunnel) to the peer. This array is populated when the `detailed` argument is used. Fields within this object can include path identifiers, latency, jitter, loss, and bandwidth metrics. |
| `peer_logical_id` | The unique logical identifier of the peer VeloCloud Edge or Gateway. |
| `peer_name` | The configured name of the peer VeloCloud Edge or Gateway. |
| `peer_type` | `VCE` if peer is a VCG or non-hub VCE.  `DCE_CLIENT` if peer is a hub edge. |
| `rx_bytes` | Number of bytes received from the peer. |
| `rx_packets` | Number of packets received from the peer. |
| `tx_bytes` | Number of bytes sent to the peer. |
| `tx_packets` | Number of packets sent to the peer. |