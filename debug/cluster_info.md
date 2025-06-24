#	--cluster_info

##	Description
Displays information about the VeloCloud Edge's clustering status. Clustering is typically used for High Availability (HA) configurations, where two Edges operate as a redundant pair to ensure network continuity. This command provides insights into the current state of such a cluster, if configured.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
The following example shows the output when clustering is not enabled on the Edge:
```
example_com:velocli> debug --cluster_info
{
  "cpu_pct": 8,
  "id": "5c715cf5-515c-4657-a45f-65c6f8f6e15b",
  "mem_pct": 29,
  "name": "DC",
  "rebalancing": false,
  "route_cnt": 1,
  "tunnel_pct": 12
}

example_com:velocli>
```
Output provides details about the cluster's state, members, and other relevant HA information.

##  Field descriptions
The output is in JSON format. The fields displayed will vary depending on whether clustering is enabled and the current state of the cluster.
| Field | Description |
|---|---|
| cpu_pct | |
| id | |
| mem_pct | |
| name | |
| rebalancing | |
| route_cnt | |
{ tunnel_pct |  |
