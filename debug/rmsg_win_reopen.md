#	--rmsg_win_reopen <logical_id>

##	Description
The `debug --rmsg_win_reopen` command is a diagnostic tool used to force the reset and reopening of a reliable messaging (rmsg) window with a specific peer entity within the VeloCloud SD-WAN fabric. Reliable messaging is a core component of VeloCloud's proprietary communication protocols, such as the VeloCloud Management Protocol (VCMP), ensuring ordered and guaranteed delivery of control and management messages. These messages are exchanged between VeloCloud Edges, Gateways, and the VeloCloud Orchestrator.

This command is typically used for troubleshooting scenarios where communication with a peer (identified by its `logical_id`) appears to be stalled, unresponsive, or experiencing errors. By forcing the rmsg window to reopen, it can help re-initialize the communication state and potentially resolve the underlying issue. This command requires the `logical_id` of the target peer to be specified.

##	Arguments
| Argument      | Description |
|---------------|-------------|
| `<logical_id>` | **Required.** The unique logical identifier of the peer entity (e.g., another VeloCloud Edge, a VeloCloud Gateway, or the VeloCloud Orchestrator) with which the reliable messaging window should be reopened. This ID is typically a universally unique identifier (UUID). |

##	Example usage
```
example_com:velocli> debug --rmsg_win_reopen
```