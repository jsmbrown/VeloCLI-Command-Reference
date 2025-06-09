#	--ike_down &lt;cookie&gt;

##	Description
For debugging purposes only. This command sets the state of specific IKE (Internet Key Exchange) Security Associations (SAs) to DOWN and attempts to restart the negotiation process. IKE SAs are typically associated with IPSec tunnels, which VeloCloud Edges use to connect to VeloCloud Hub Edges, VeloCloud Gateways, or Non-VeloCloud Sites (NVS/NSD). The target SA is identified by its cookie, which must be provided in hexadecimal format.

##	Arguments
| Argument   | Description                                                                                                |
|------------|------------------------------------------------------------------------------------------------------------|
| `<cookie>` | Mandatory. The IKE SA cookie, specified in hexadecimal format (e.g., `a1b2c3d4e5f6a7b8` or `0xa1b2c3d4e5f6a7b8`). This cookie uniquely identifies an active IKE session that needs to be reset. |

##	Example Usage
```
example_com:velocli> debug --ike_down
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
**Note:** The example above shows the command being invoked without the mandatory `<cookie>` argument. In such cases, the system typically displays the help/usage instructions for the `debug.py` script, as shown in the output. A correct invocation would include a specific IKE cookie, for example: `debug --ike_down a1b2c3d4e5f6a7b8`.

##	Field Descriptions
This command performs an administrative action on an IKE session. It does not produce tabular data output. Success or failure of the action is typically indicated by a console message (not shown in the provided example output). The example output demonstrates the help text that is often displayed when mandatory arguments for a command are omitted.