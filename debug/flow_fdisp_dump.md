#	--flow_fdisp_dump [<flowId>]

##	Description
Dump flow dispatcher flows. If a `flowId` is provided, it will dump flows associated with that particular flow classifier (fc).

##  Arguments (optional)
| Argument | Description |
|---|---|
| `flowId` |  (Optional) The specific flow ID to filter the flow dispatcher dump. If not provided, all flow dispatcher flows are dumped. |

##  Example usage
```
example_com:velocli> debug --flow_fdisp_dump
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
**Note:** The example output provided is a usage/help message, typically displayed when a command is run with incorrect parameters or when help is invoked. The actual output of `debug --flow_fdisp_dump` would list flow dispatcher entries.

##  Field descriptions
| Column | Description |
|---|---|
|   |  (Actual output fields for `debug --flow_fdisp_dump` are not available in the provided example.)  |