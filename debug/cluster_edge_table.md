#	--cluster_edge_table

##	Description
This command displays the mapping table between clusters and the VeloCloud Edges associated with them. In a VeloCloud SD-WAN deployment, Edges can be grouped into clusters for high availability and scalability. This table provides a quick overview of these relationships.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --cluster_edge_table
[]
```
In this example, the output `[]` indicates that there are currently no cluster-to-edge mappings configured or active on this particular VeloCloud Edge, or the command is run on a non-clustered Edge.

##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example output `[]` indicates an empty table, meaning there are no specific fields to describe for this output. If clusters and edges were mapped, the output would typically list cluster identifiers and their corresponding edge identifiers. |