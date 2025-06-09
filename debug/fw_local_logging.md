# --fw_local_logging [enable|disable|status]

## Description
Manages the local logging state for the firewall on the VeloCloud Edge. Use `enable` to activate local logging, `disable` to deactivate it, and `status` to retrieve the current logging state. This feature is useful for detailed troubleshooting of firewall behavior directly on the appliance by inspecting logs stored locally.

## Arguments
| Argument | Description |
|---|---|
| `enable`   | Enables local firewall logging on the Edge. When enabled, firewall-related events are logged locally on the appliance. |
| `disable`  | Disables local firewall logging on the Edge. This stops the local collection of firewall event logs. |
| `status`   | Displays the current status (enabled or disabled) of local firewall logging on the Edge. |

## Example usage
The following example shows the output when `debug --fw_local_logging` is run without specifying one of the required arguments (`enable`, `disable`, or `status`). In this scenario, the system displays the general help message for the `debug.py` script, as the command requires one of these arguments to perform a specific action.
```
example_com:velocli> debug --fw_local_logging
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A typical successful invocation would be, for example, `debug --fw_local_logging status`, which would then output the current status of local firewall logging (e.g., "Local firewall logging is enabled.").

## Field descriptions
| Column | Description |
|---|---|
|   | The example output provided shows the general usage help for the `debug.py` script. This output is displayed because the `debug --fw_local_logging` command was invoked without one of its mandatory arguments (`enable`, `disable`, or `status`). A successful execution of this command with a valid argument (e.g., `debug --fw_local_logging status`) typically yields a direct textual response indicating the outcome or current state (e.g., "Local firewall logging is enabled" or "Local firewall logging is disabled"). Such output is not tabular and therefore does not have distinct fields or columns. |