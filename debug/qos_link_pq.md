#	--qos_link_pq [ on | off | status ]

##	Description
Manages the Link Quality of Service (QoS) Priority Queue feature on the VeloCloud Edge. This feature allows for the prioritization of critical traffic types by placing them into a priority queue for transmission over the SD-WAN paths. This ensures that high-priority applications receive preferential treatment, especially during periods of network congestion. Use this command to enable, disable, or check the current operational status of the Link QoS Priority Queue.

##  Arguments
| Argument | Description |
|---|---|
| `on` | Enables the Link QoS Priority Queue. |
| `off` | Disables the Link QoS Priority Queue. |
| `status` | Displays the current status (e.g., enabled or disabled) of the Link QoS Priority Queue. |

##  Example usage

To check the current status of the Link QoS Priority Queue:
```
example_com:velocli> debug --qos_link_pq status
Link QoS Priority Queue: Enabled
```

To enable the Link QoS Priority Queue:
```
example_com:velocli> debug --qos_link_pq on
Link QoS Priority Queue has been enabled.
```

To disable the Link QoS Priority Queue:
```
example_com:velocli> debug --qos_link_pq off
Link QoS Priority Queue has been disabled.
```

If `--qos_link_pq` is invoked without one of the required arguments (`on`, `off`, `status`), it may display usage information for the parent `debug` command or an error, as suggested by the provided context:
```
example_com:velocli> debug --qos_link_pq
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##  Field descriptions
This command does not produce tabular output with distinct fields. The output is typically a status message (e.g., "Link QoS Priority Queue: Enabled") or a confirmation of the action taken (e.g., "Link QoS Priority Queue has been enabled.").