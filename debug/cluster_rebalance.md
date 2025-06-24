# --cluster_rebalance [rebalance_type]

## Description
This command is executed on a VeloCloud Hub Edge within a cluster to initiate a re-distribution of its connected spoke Edges. The goal is to achieve a more uniform distribution of spokes across the Hubs in the cluster. The rebalance behavior depends on the specified `rebalance_type`.

## Arguments
| Argument        | Description                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rebalance_type`  | Specifies the mode of cluster rebalancing. This argument is mandatory. Valid values are:<ul><li>`include-self`: Triggers a rebalance operation aiming for a uniform distribution of spoke Edges across all Hubs in the cluster, including the Hub Edge where the command is executed.</li><li>`exclude-self`: Triggers a rebalance operation where the Hub Edge executing the command attempts to offload its connected spoke Edges to other Hubs in the cluster. This aims for a uniform distribution of spokes among the *other* Hubs.</li></ul> |

## Example usage
```
To trigger a rebalance that includes the current Hub in the distribution:
```
example_com:velocli> debug --cluster_rebalance include-self

{

  "Rebalance cluster": "Cluster rebalance request sent to gateway"

}

```

To trigger a rebalance that excludes the current Hub, offloading its spokes:
```
example_com:velocli> debug --cluster_rebalance exclude-self

{

  "Rebalance cluster": "Cluster rebalance request sent to gateway"

}

```
*(Note: The exact output messages for successful initiation may vary.)*

## Field descriptions
This command does not produce tabular output. Upon successful execution, it typically returns a confirmation message indicating that the cluster rebalance process has been initiated. The actual rebalancing process occurs in the background.
