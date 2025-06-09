#	--memory_leak [num of MB to leak]

##	Description
Deliberately causes memory to be leaked inside the VeloCloud Edge. This command is intended for advanced debugging and testing scenarios to observe system behavior under memory pressure.

##  Arguments (optional)
| Argument            | Description |
|---------------------|-------------|
| `[num of MB to leak]` | Optional. Specifies the amount of memory in megabytes (MB) that the Edge daemon should deliberately leak. Replace `[num of MB to leak]` with a numerical value (e.g., `100` for 100MB). If this argument is omitted, the command might leak a default amount of memory, or its behavior may vary (the provided example usage shows the command invoked without this argument, followed by a general usage message). |

##  Example usage
```
example_com:velocli> debug --memory_leak
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##  Field descriptions
| Item                  | Description |
|-----------------------|-------------|
| Command Output        | This command does not produce specific data columns or tabular output in the console upon successful execution. It is an action-triggering command designed to affect system state. |
| Observable Effect     | The primary effect is increased memory consumption on the VeloCloud Edge. This change must be monitored using system resource utilities or other diagnostic tools on the Edge. |
| Example Output Context| The output shown in the "Example usage" section is a general help/usage message for the `debug.py` script. This type of message may appear if a command is entered with incorrect syntax, missing required parameters, or if the specific subcommand is not recognized in that context. It does not represent the direct outcome of a successful memory leak operation. |