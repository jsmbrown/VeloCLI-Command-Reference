#	--set_link_state_up [interface logical name]

##	Description
This command is used to manually set the internal software state of a specified network interface on the VeloCloud Edge to 'UP'. This can be useful for diagnostic or testing purposes, allowing an administrator to override the current perceived state of a link. It's important to note that this command affects the Edge's software interpretation of the link status and does not change the physical state of the interface itself.

##  Arguments
| Argument                 | Description                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| `interface logical name` | **Required.** Specifies the logical name of the interface whose state is to be set to UP (e.g., `GE1`, `SFP1`, `eth0`). |

##  Example Usage
The following example demonstrates the output when the `debug --set_link_state_up` command is invoked without the mandatory `interface logical name` argument. In such cases, the system displays the help or usage information for the parent `debug.py` script, indicating that a required argument is missing.
```
example_com:velocli> debug --set_link_state_up
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A successful execution of this command (e.g., `debug --set_link_state_up GE1`) would typically result in a confirmation message or no output if the operation is successful. The exact output for a successful command may vary.