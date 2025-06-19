#	--sched_xstats [enable|disable]

##	Description
Enable/Disable scheduled extended statistics. These statistics can provide more detailed insights into network performance and behavior, complementing standard monitoring data.

##	Arguments
| Argument | Description |
|---|---|
| enable | Enables the collection and processing of scheduled extended statistics. |
| disable | Disables the collection and processing of scheduled extended statistics. |

##	Example usage
```
example_com:velocli> debug --sched_xstats
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##	Field descriptions
The output shown in the example is the usage message for the `debug.py` script. It lists available arguments and subcommands for `debug.py`. For descriptions of fields or outputs related to other commands (e.g., if `enable` or `disable` were used and produced specific output), please refer to their respective documentation entries or observe the command's output upon successful execution. Typically, a successful execution of `debug --sched_xstats enable` or `debug --sched_xstats disable` would result in a confirmation message.