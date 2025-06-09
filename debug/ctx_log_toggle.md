#	`--ctx_log_toggle [all|TID] [1|0]`

##	Description
The `--ctx_log_toggle` command enables or disables context logging for threads on the VeloCloud Edge. Context logging provides detailed, thread-specific information useful for diagnostics. The command requires specifying a target for the logging (either all threads or a specific Thread ID) and the desired state (enable or disable).

##  Arguments
The command requires two positional arguments:

| Argument         | Description                                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `all` or `TID`   | (First positional argument, required) Specifies the target for context logging. <br> - `all`: Applies the logging state to all threads. <br> - `TID`: Applies the logging state to a specific thread, identified by its Thread ID. Replace `TID` with the actual numerical thread identifier. |
| `1` or `0`       | (Second positional argument, required) Specifies the action for context logging. <br> - `1`: Enables context logging for the specified target. <br> - `0`: Disables context logging for the specified target. |

##  Example usage
The following example shows the output when `debug --ctx_log_toggle` is invoked without its required arguments. This typically results in the display of the help message for the parent `debug.py` script.
```
example_com:velocli> debug --ctx_log_toggle
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A correct invocation would be, for example, `debug --ctx_log_toggle all 1` to enable logging for all threads, or `debug --ctx_log_toggle 12345 0` to disable logging for thread ID 12345.

##  Field descriptions
This command is used to perform an action (toggling logging status) and does not produce tabular output with distinct fields. The example output shown is the general usage help for the `debug.py` script, which is displayed because `debug --ctx_log_toggle` was called without its own required arguments. A successful execution of `--ctx_log_toggle` with valid arguments would likely result in a confirmation message (e.g., "Context logging enabled for all threads") rather than a table of data.