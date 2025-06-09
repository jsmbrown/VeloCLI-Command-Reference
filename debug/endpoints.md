#	--endpoints [v4 | v6 | all]

##	Description
Dumps the current VeloCloud Management Protocol (VCMP) endpoint table. This table lists the source and destination IP addresses for active VCMP sessions, which are used for management and control plane communication between VeloCloud Edges and VeloCloud Gateways or the VeloCloud Orchestrator.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4 | Display only IPv4 VCMP endpoints. |
| v6 | Display only IPv6 VCMP endpoints. |
| all | Display all VCMP endpoints (both IPv4 and IPv6). This is the default if no argument is specified. |
| none | If no argument is specified, it defaults to displaying all VCMP endpoints. |

##  Example usage
```
example_com:velocli> debug --endpoints
src_ip              dst_ip
216.221.31.44   172.30.0.6
170.85.14.130   172.30.0.6
216.221.27.88   172.30.0.6
```

##  Field descriptions
| Column | Description |
|---|---|
| src_ip | The source IP address of the VCMP session. This is typically the IP address of the VeloCloud Edge. |
| dst_ip | The destination IP address of the VCMP session. This is typically the IP address of a VeloCloud Gateway or the VeloCloud Orchestrator. |