# --pr_rr_reg &lt;gw_logicalid&gt; &lt;peer_id&gt;

## Description
Registers a request to initiate a VeloCloud Routing Protocol (VCRP) route refresh for a specified remote peer. The remote peer is typically another VeloCloud Edge or a Non-VeloCloud Site (NVS/NSD) connected via a VeloCloud Gateway.

This command forces the local VeloCloud Edge to request an update of routing information from the specified peer through the designated gateway. It is primarily used for diagnostic and troubleshooting purposes, for instance, when routes from a particular peer are suspected to be stale, missing, or not correctly propagated within the SD-WAN overlay network. Triggering a route refresh can help ensure the local Edge has the most current routing state from the peer.

## Arguments
| Argument         | Description                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `&lt;gw_logicalid&gt;` | **Mandatory.** The logical identifier (ID) of the VeloCloud Gateway through which the connection to the remote peer is established. This ID uniquely identifies the gateway within the VeloCloud Orchestrator. |
| `&lt;peer_id&gt;`      | **Mandatory.** The unique identifier (ID) of the remote peer (e.g., another VeloCloud Edge or an NVS) for which the route refresh is being requested.                               |

## Example usage
```
example_com:velocli> debug --pr_rr_reg gw-01234567-89ab-cdef-0123-456789abcdef 1a2b3c4d-5e6f-7a8b-9c0d-1e2f3a4b5c6d
Route refresh successfully registered for peer 1a2b3c4d-5e6f-7a8b-9c0d-1e2f3a4b5c6d via gateway gw-01234567-89ab-cdef-0123-456789abcdef.
```

## Field descriptions
This command does not produce tabular output.
*   On successful execution, it typically returns a confirmation message indicating that the route refresh request has been registered.
*   If the command fails (e.g., due to invalid `gw_logicalid` or `peer_id`, or if the peer/gateway is unreachable), an error message detailing the failure will be displayed.