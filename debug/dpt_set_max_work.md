#	--dpt_set_max_work &lt;core-id|all&gt; &lt;match&gt; &lt;max_work&gt;

##	Description
Set the maximum work allowed for a specific Data Plane (DP) task. This command is used to control the processing resources allocated to individual tasks running on the VeloCloud Edge's data plane cores. Adjusting `max_work` can help in performance tuning or troubleshooting scenarios where a particular task might be consuming excessive resources.

##  Arguments
| Argument | Description |
|---|---|
| &lt;core-id\|all&gt; | Specifies the target core for the setting. Use a numerical core ID (e.g., `0`, `1`) or `all` to apply the setting to all data plane cores. |
| &lt;match&gt; | A string used to identify the specific Data Plane task. This could be a task name or a pattern that matches the task. |
| &lt;max_work&gt; | An integer value representing the maximum work units the specified task is allowed to consume per scheduling cycle. |

##  Example usage
```
example_com:velocli> debug --dpt_set_max_work
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
**Note:** The example above shows the output when the command is run without the required arguments, displaying the help/usage message. A complete command would look like:
`example_com:velocli> debug --dpt_set_max_work all some_task_identifier 1000`

##  Field descriptions
This command does not produce tabular output with specific fields to describe. Its primary function is to set a configuration value, and its output upon successful execution is typically minimal or confirmatory. The example usage provided shows the help text displayed when arguments are missing.