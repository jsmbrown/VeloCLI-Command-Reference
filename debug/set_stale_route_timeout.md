#	--set_stale_route_timeout [timeout]

##	Description
Sets the stale refresh timeout in minutes. This timeout value determines how long the system will wait before refreshing stale route information. The value must be between 1 and 60 minutes.

##  Arguments
| Argument | Description |
|---|---|
| timeout | Specifies the timeout duration in minutes. Must be an integer between 1 and 60 (inclusive). |

##  Example usage
To set the stale route timeout to 30 minutes:
```
example_com:velocli> debug --set_stale_route_timeout 30
```
If the command is entered without the required timeout argument, or with an invalid value, it may display usage instructions or an error message. For example, the provided sample output:
```
example_com:velocli> debug --set_stale_route_timeout
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
This output indicates that the command was likely invoked incorrectly (e.g., without the mandatory `timeout` argument) and the system responded with a general help message for the `debug.py` script.

##  Field descriptions
This command does not produce tabular output. It modifies a system configuration value.