#	--logger_setsquelching <on|off> [max=<value>]

##	Description
This command is used to enable or disable log squelching on the VeloCloud Edge. Log squelching helps manage log volume by preventing highly repetitive log messages from flooding the logs. When enabled, it can limit the number of times an identical, consecutive log message is written. This command also allows setting a maximum threshold for the number of such entries before squelching is applied.

##  Arguments
| Argument | Description |
|---|---|
| `<on\|off>` | **Required.** Specifies the desired state of log squelching. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`on`: Enables log squelching. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`off`: Disables log squelching. |
| `max=<value>` | **Optional.** Sets the maximum number of identical, consecutive log entries that will be recorded before squelching takes effect for that specific message. `<value>` should be a positive integer (e.g., `max=1000`). This argument is typically used in conjunction with `on`. If squelching is enabled (`on`) and `max` is not specified, a system default value may be used. |

##  Example usage
To enable log squelching (using the system default for the maximum number of entries):
```
example_com:velocli> debug --logger_setsquelching on
```

To enable log squelching and set the maximum number of identical consecutive entries to 500 before squelching applies:
```
example_com:velocli> debug --logger_setsquelching on max=500
```

To disable log squelching:
```
example_com:velocli> debug --logger_setsquelching off
```
The example below shows the help output if the command is entered without the required `on` or `off` argument:
```
example_com:velocli> debug --logger_setsquelching
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ... (additional help output truncated) ...
```

##  Field descriptions
This command is used to configure a system setting and does not produce tabular output. Successful execution typically results in a confirmation message or a change in logging behavior, which can be observed in the system logs.