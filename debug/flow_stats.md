#	--flow_stats [&lt;peer_id&gt;]

##	Description
Displays statistics for active network flows, categorized by the type of path they traverse (e.g., Edge to Cloud direct, Edge to Edge direct) and by protocol (TCP, UDP, ICMP, Other). This command helps in understanding traffic distribution across different SD-WAN paths.

##  Arguments (optional)
| Argument | Description |
|---|---|
| &lt;peer_id&gt; | The identifier of a specific peer (Edge or Gateway). If provided, flow statistics will be filtered to show only flows involving this peer. If omitted, aggregate flow statistics for all peers are displayed. |

##  Example usage
```
example_com:velocli> debug --flow_stats
Path                           Total Flows  TCP Flows  UDP Flows  ICMP Flows  Other Flows
Edge2CloudViaGateway                     0          0          0           0            0
Edge2CloudDirect                        21         14          7           0            0
Edge2EdgeViaGateway                      0          0          0           0            0
Edge2EdgeViaHub                          0          0          0           0            0
Edge2EdgeDirect                          0          0          0           0            0
```

##  Field descriptions
| Column | Description |
|---|---|
| Path | The classification of the SD-WAN path taken by the flows. Examples include: <br> - `Edge2CloudViaGateway`: Traffic from the Edge to a cloud service, routed through a VeloCloud Gateway. <br> - `Edge2CloudDirect`: Traffic from the Edge directly to a cloud service over a local internet breakout. <br> - `Edge2EdgeViaGateway`: Traffic between two VeloCloud Edges, routed through a VeloCloud Gateway. <br> - `Edge2EdgeViaHub`: Traffic between two VeloCloud Edges, routed through a Hub Edge. <br> - `Edge2EdgeDirect`: Traffic directly between two VeloCloud Edges (Dynamic Edge to Edge tunnels). |
| Total Flows | The total number of active flows traversing this type of path. |
| TCP Flows | The number of active TCP flows traversing this type of path. |
| UDP Flows | The number of active UDP flows traversing this type of path. |
| ICMP Flows | The number of active ICMP flows traversing this type of path. |
| Other Flows | The number of active flows using protocols other than TCP, UDP, or ICMP traversing this type of path. |