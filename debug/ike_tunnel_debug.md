#	`--ike_tunnel_debug [clear | <src-ip> <dest-ip> <level>]`

##	Description
Enables or disables per-tunnel debugging for Internet Key Exchange (IKE) sessions. This command allows for targeted troubleshooting of IKE negotiations between specific IP endpoints. When debugging is enabled for a specific source and destination IP pair, detailed IKE protocol messages and events for that tunnel will be logged. The `clear` option disables all previously enabled per-tunnel IKE debugging.

This is particularly useful for diagnosing issues with IPSec tunnel establishment to Non-VeloCloud Sites (NVS/NSD) or other Edges/Gateways where IKE negotiation problems are suspected.

##	Arguments
| Argument | Description |
|---|---|
| `clear` | Disables all active per-tunnel IKE debugging sessions. This will stop the generation of detailed IKE logs for any previously specified tunnels. |
| `<src-ip>` | The source IP address of the VeloCloud Edge initiating or responding to the IKE negotiation for the specific tunnel to be debugged. |
| `<dest-ip>` | The destination IP address of the remote peer (e.g., NVS, another Edge, or Gateway) for the specific IKE tunnel to be debugged. |
| `<level>` | An integer value specifying the verbosity level for the debug output. Higher numbers generally correspond to more detailed and extensive logging. The exact range and meaning of levels can vary, but typically a level like 1, 2, or 3 would provide increasing amounts of detail. |

##	Example Usage
**To enable IKE debugging for a specific tunnel (e.g., source 10.0.0.1 to destination 203.0.113.5 at debug level 2):**
```
example_com:velocli> debug --ike_tunnel_debug 10.0.0.1 203.0.113.5 2
IKE debugging enabled for tunnel 10.0.0.1 <-> 203.0.113.5 at level 2.
```

**To clear/disable all per-tunnel IKE debugging:**
```
example_com:velocli> debug --ike_tunnel_debug clear
All per-tunnel IKE debugging disabled.
```

**Example of insufficient arguments (as provided in the prompt):**
```
example_com:velocli> debug --ike_tunnel_debug
Insufficient Arguments. Refer --help.
```

##	Notes
*   Enabling IKE debugging, especially at higher verbosity levels, can generate a significant volume of log data. This may consume system resources and potentially impact performance.
*   It is recommended to enable debugging only for the duration of active troubleshooting and to disable it promptly once the necessary information has been collected.
*   The debug output is typically written to the system logs or a specific IKE/VPN log file on the VeloCloud Edge. Consult the Edge's logging mechanisms to view the generated debug messages.
*   This command is essential for troubleshooting complex IPSec VPN connectivity issues where standard logs do not provide sufficient detail about the IKE negotiation phases (Phase 1 and Phase 2).