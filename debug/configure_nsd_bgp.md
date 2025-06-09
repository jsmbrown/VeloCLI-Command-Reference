#	--configure_nsd_bgp

##	Description
This command is intended for configuring Border Gateway Protocol (BGP) settings related to Non-SD-WAN Destinations (NSD) on a VeloCloud Edge. However, the command is currently marked as **unsupported**. Attempting to use this command will typically display a general usage help message for the `debug.py` utility, as shown in the example below.

Non-SD-WAN Destinations (NSD) refer to non-VeloCloud sites that Edges or Gateways connect to, often via IPSec or GRE tunnels, and may require BGP for dynamic routing.

##	Arguments
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##	Example usage
```
example_com:velocli> debug --configure_nsd_bgp
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##	Field descriptions
This command does not produce specific output fields related to NSD BGP configuration. As indicated in the example usage, it is unsupported and typically displays a general help message for the `debug.py` script, not tabular data with specific fields.