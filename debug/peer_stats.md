#	--peer_stats `[ <peer_id> | all ] [detailed | all]`

##	Description
Displays statistics for each peer VeloCloud Edge or Gateway. The `detailed` option provides additional path statistics for each tunnel established with the peer. This information is useful for monitoring the health and performance of connections to other SD-WAN nodes in the overlay network.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<peer_id>` | Specifies the logical ID of a particular peer for which to display statistics. |
| `all` (first argument) | Displays statistics for all known peers. This is the default if no peer ID is specified. |
| `detailed` | Includes detailed path statistics for each tunnel associated with the peer(s). This includes metrics like latency, jitter, packet loss, and bandwidth for individual paths. |
| `all` (second argument) | When used as the second argument, it implies showing all available information, which is effectively the same as `detailed` if a peer ID is specified, or detailed information for all peers if the first argument is also `all` or omitted. If only one `all` is provided, it's interpreted as the first argument (all peers). |

##  Example usage
```
example_com:velocli> debug --peer_stats
{
  "peer_stats_dump": [
    {
      "path_stats": [],
      "peer_logical_id": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8",
      "peer_name": "vcg44-dfw1"
    }
    // ... more peers ...
  ]
}
```
**Example with `detailed` option (conceptual output structure):**
```
example_com:velocli> debug --peer_stats <peer_id> detailed
{
  "peer_stats_dump": [
    {
      "path_stats": [
        {
          "path_id": "some_path_id_1",
          "tunnel_id": "some_tunnel_id_1",
          "latency_ms": 10,
          "jitter_ms": 2,
          "loss_percentage": 0.1,
          "tx_bps": 1000000,
          "rx_bps": 500000
          // ... other path specific stats ...
        }
      ],
      "peer_logical_id": "2bbfbb2b-4ee0-46a1-b394-01d8194f97b8",
      "peer_name": "vcg44-dfw1"
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