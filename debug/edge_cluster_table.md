#	--edge_cluster_table

##	Description
Dumps the edge cluster mapping table. This table shows the association of VeloCloud Edges (VCEs) to their respective clusters. Edge clustering is typically used for High Availability (HA) and resilience.

##	Arguments (optional)
This command takes no arguments.

##	Example usage
```
example_com:velocli> debug --edge_cluster_table
VCE-ID   ClusterId  Dir
```

##	Field descriptions
| Column    | Description |
|-----------|-------------|
| VCE-ID    | VeloCloud Edge Identifier. The unique identifier for the VeloCloud Edge. |
| ClusterId | Cluster Identifier. The identifier of the cluster to which the VeloCloud Edge belongs. Edges are often grouped into clusters for High Availability (HA) or load distribution. |
| Dir       | This field indicates a specific attribute, role, or status of the Edge in relation to its membership within the cluster. The exact interpretation may depend on the specific clustering model and configuration (e.g., it could denote an operational state, a role like active/standby in some contexts, or a configuration parameter). |