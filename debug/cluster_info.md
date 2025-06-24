#	--cluster_info

##	Description
Displays information about the VeloCloud Edge's clustering status. Clustering is typically used for redundant configurations, where two or more Edges operate as Active Hubs to ensure network continuity. This command provides insights into the current state of such a cluster, if configured.

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

##  Field descriptions
The output is in JSON format. The fields displayed will vary depending on whether clustering is enabled and the current state of the cluster.
| Field | Description |
|---|---|
| cpu_pct | CPU percent utilization of the Hub |
| id | ID of the cluster |
| mem_pct | Percent memory utilization of the Hub |
| name | Name of the Cluster |
| rebalancing | True or False if Auto Rebalancing is enabled for the Cluster |
| route_cnt | Route count of the Hub |
| tunnel_pct | Percent of tunnels the Hub supports |
