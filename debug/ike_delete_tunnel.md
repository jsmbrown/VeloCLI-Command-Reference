#	--ike_delete_tunnel &lt;cookie&gt;

##	Description
Deletes an active IKE (Internet Key Exchange) tunnel. The tunnel is identified by its IKE cookie, which must be provided in hexadecimal format. IKE is a fundamental part of IPSec VPNs, used to negotiate security parameters and establish secure channels between VeloCloud Edges, Gateways, or Non-VeloCloud Sites (NVS/NSD). This command can be used to manually tear down a specific IKE session, often for troubleshooting purposes or to force a re-negotiation.

##  Arguments
| Argument   | Description                                                                                                                                    |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| `<cookie>` | **Required.** The IKE cookie of the tunnel to be deleted. This value must be specified in hexadecimal format (e.g., `0x1a2b3c4d5e6f7890`). The IKE cookie is a unique identifier for an IKE Security Association (SA). |

##  Example usage
To delete an IKE tunnel with a specific cookie:
```
example_com:velocli> debug --ike_delete_tunnel 0x1a2b3c4d5e6f7890
```
If the command is successful, it will typically result in the specified IKE tunnel being torn down. If the cookie is not found or an error occurs, an appropriate message may be displayed. The command itself does not produce detailed tabular output upon successful execution.

If the required `<cookie>` argument is omitted, the system will display usage information for the `debug` command, as shown in the generic help output:
```
example_com:velocli> debug --ike_delete_tunnel
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ...
```

##  Field descriptions
This command does not produce a tabular output with specific fields. Output is generally limited to a success or failure message.