#	`--peer_routes [all|v4|v6]`

##	Description
Displays the peer route table, which contains routes learned from other VeloCloud Edges within the SD-WAN overlay network via protocols like VeloCloud Routing Protocol (VCRP). These routes facilitate direct Edge-to-Edge communication, either dynamically established (DE2E) or through static configurations to hub Edges. This command helps in verifying routing information exchanged between peer Edges.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no argument is specified) Displays all peer routes, including both IPv4 and IPv6. |
| `v4` | Displays only IPv4 peer routes. |
| `v6` | Displays only IPv6 peer routes. |

##  Example usage
```
example_com:velocli> debug --peer_routes
{
  "routes": []
}
```
The example above shows a scenario where there are currently no active peer routes on the Edge. If peer routes were present, the `routes` array would be populated.

##  Field descriptions
The output is in JSON format. The `routes` array will contain objects, each representing a peer route learned from another VeloCloud Edge. While the provided example shows an empty list (indicating no peer routes at the time of command execution), a populated list would include details for each peer route. These details are generally a subset of or similar to the information provided by the `debug --routes` command, but specifically filtered for routes learned from peer Edges.

Expected fields within each route object typically include:
*   **Destination Prefix/Address:** The IP address or network prefix of the route.
*   **Netmask:** The subnet mask for the destination prefix.
*   **Next Hop Information:** Details about the peer VeloCloud Edge from which this route is learned (e.g., peer name, logical ID).
*   **Metrics:** Routing metrics associated with the path to the peer (e.g., cost, preference).
*   **Type:** Indication that the route is a peer route (e.g., "edge2edge").
*   **Segment ID:** The network segment to which this route belongs.
*   **Flags:** Additional properties or status of the route.

For a comprehensive understanding of all possible route fields and flags, refer to the documentation for the `debug --routes` command.