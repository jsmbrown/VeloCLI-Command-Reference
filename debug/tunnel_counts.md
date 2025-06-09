#	--tunnel_counts [logical-id | all]

##	Description
Dumps the tunnel count of connected VeloCloud Edges. This command is used to ascertain the number of active SD-WAN tunnels the local Edge has established with its peers, which can include other VeloCloud Edges or VeloCloud Gateways. This information is useful for verifying connectivity and understanding the current state of the overlay network paths.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `logical-id` | If specified, the command displays tunnel count information for the peer VeloCloud Edge or Gateway identified by this unique logical ID. |
| `all` | Displays tunnel counts for all peer VeloCloud Edges and Gateways connected to the local Edge. This is generally the default behavior if no argument is specified. |
| *none* | If no argument is provided, the command typically defaults to displaying tunnel counts for all connected peer Edges and Gateways (similar to specifying `all`). |

##  Example usage
```
example_com:velocli> debug --tunnel_counts
```

##  Field descriptions
*(The specific output format and fields for this command were not provided in the input. The output would typically list peer Edges/Gateways and their respective tunnel counts to the local Edge.)*