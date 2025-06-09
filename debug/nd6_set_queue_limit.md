#	--nd6_set_queue_limit <limit>

##	Description
Sets the queue limit per neighbor for IPv6 Neighbor Discovery (ND) protocol operations. This command helps in managing the resources on the VeloCloud Edge by limiting the number of ND packets (e.g., Neighbor Solicitations, Neighbor Advertisements) that can be queued for processing per IPv6 neighbor. This can be useful in preventing resource exhaustion under certain network conditions or when dealing with unresponsive or misbehaving neighbors.

##  Arguments
| Argument | Description |
|---|---|
| `<limit>` | (Required) An integer value specifying the maximum number of IPv6 Neighbor Discovery packets that can be queued for a single neighbor. This value dictates how many unresolved neighbor discovery requests or responses can be buffered for that specific neighbor. |

##  Example usage
This example sets the Neighbor Discovery queue limit per neighbor to 64 packets.
```
example_com:velocli> debug --nd6_set_queue_limit 64
Successfully set ND6 per-neighbor queue limit to 64.
```
If the `<limit>` argument is not provided, the command will typically display usage information:
```
example_com:velocli> debug --nd6_set_queue_limit
usage: debug.py nd6_set_queue_limit <limit>
debug.py nd6_set_queue_limit: error: the following arguments are required: limit
```

##  Field descriptions
This command is used to configure a system parameter related to IPv6 Neighbor Discovery. It does not produce tabular output.
*   Upon successful execution, it typically displays a confirmation message indicating the new queue limit.
*   If the required `<limit>` argument is missing or invalid, an error message or usage instructions will be displayed, as shown in the second example above.