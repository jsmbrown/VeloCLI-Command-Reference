#	--vcrp_win_reopen <logical_id>

##	Description
This command instructs the VeloCloud Edge to reopen the VeloCloud Routing Protocol (VCRP) window with a specified peer. VCRP is a proprietary protocol used for exchanging routing information and managing session state within the SD-WAN overlay. Reopening the VCRP window can be used as a troubleshooting step to reset and re-initialize the VCRP communication state with a specific VeloCloud peer (another Edge or a Gateway) identified by its logical ID. This action can help resolve issues related to VCRP peering, session establishment, or stale routing information between the devices.

##  Arguments
| Argument | Description |
|---|---|
| `<logical_id>` | **Required.** The logical ID of the VeloCloud peer (Edge or Gateway) with which to reopen the VCRP window. This is a unique identifier for the remote VeloCloud device in the SD-WAN fabric. |

##  Example usage
To reopen the VCRP window with a peer identified by the logical ID `3294602a-5a69-4694-a7d2-811aff737faa`:
```
example_com:velocli> debug --vcrp_win_reopen 3294602a-5a69-4694-a7d2-811aff737faa
```
This command attempts to reopen the VCRP window with the specified peer. It typically does not produce direct output upon successful execution but may return an error message if the operation fails (e.g., the logical ID is invalid or the peer is unreachable).

If the mandatory `<logical_id>` argument is omitted, the system will display a usage help message similar to the following:
```
example_com:velocli> debug --vcrp_win_reopen
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ... (output truncated for brevity)
```

##  Field descriptions
This command is an operational command used to trigger an action and does not produce tabular output.