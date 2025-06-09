# --logfile LOGFILE

## Description
Configures the VeloCloud Edge to redirect the output of subsequent `debug` commands to the specified `LOGFILE` instead of displaying it on the console. This allows for persistent storage and later analysis of debug information.

## Arguments
| Argument  | Description                                                                                                                                                              |
| :-------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `LOGFILE` | The name of the file (e.g., `edge_debug_session.log`) where debug output will be written. The file is created on the Edge's local filesystem. If the file already exists, it is typically overwritten. |

## Example Usage
To redirect debug output to a file named `my_debug_logs.txt`:
```
example_com:velocli> debug --logfile my_debug_logs.txt
```
**Note:** This command itself does not produce any output on the console. After this command is successfully executed, any subsequent `debug` commands (e.g., `debug.py --links`, `debug.py --routes`) run in the same session will write their output to the `my_debug_logs.txt` file on the VeloCloud Edge. To view the logs, you would need to access this file on the Edge's filesystem (e.g., via SCP, or if other CLI commands allow displaying file contents).

## Field Descriptions
This command does not produce any direct console output or tabular data. Its sole purpose is to configure the log file destination for other `debug` commands executed within the current `velocli` session.