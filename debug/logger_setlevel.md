# --logger_setlevel &lt;level_num&gt; [module=&lt;moduleName&gt;[,&lt;moduleName&gt;[,...]]] [logX]

## Description
Overrides the default log level for specified system modules on a VeloCloud Edge. This command allows administrators to dynamically adjust the verbosity of logs for troubleshooting or monitoring purposes. The syntax for using this command to set a log level is `debug --logger_setlevel <level_num> [module=<moduleName>[,<moduleName>[,...]]] [logX]`. If called without the required arguments, it may display usage information.

## Arguments
| Argument | Description |
|---|---|
| `<level_num>` | **(Required)** The numerical value for the desired log level. Typically, these levels correspond to standard syslog priorities (e.g., 0 for Emergency, 5 for Notice, 7 for Debug). |
| `module=<moduleName>[,<moduleName>[,...]]` | (Optional) Specifies the target module or a comma-separated list of modules for which the log level should be changed. If this argument is omitted, the log level change might apply to a default set of modules or all modules, depending on the system's behavior. Example: `module=VCMP,EDGE_EVENT`. |
| `logX` | (Optional) An additional logging parameter or flag. The specific meaning of `X` (e.g., a numerical identifier or a specific keyword) and its effect on logging behavior (such as directing logs to a specific file or enabling a particular logging feature) would be specific to the VeloCloud Edge's logging subsystem. |

## Example usage
The following example shows the output when `debug --logger_setlevel` is entered without the required `<level_num>` argument. This typically results in the system displaying general usage instructions for the `debug.py` script.

```
example_com:velocli> debug --logger_setlevel
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

To actually set a log level, you would provide the arguments as described. For instance, to set the log level for the `VCMP` module to debug (assuming 7 is debug):
```
example_com:velocli> debug --logger_setlevel 7 module=VCMP
```
*(The output of a successful log level change is typically a confirmation message or no output if the command executes silently.)*