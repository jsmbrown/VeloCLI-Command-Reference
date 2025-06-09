#	--vnf_ha_suppress

##	Description
This command activates a suppression mechanism for VNF (Virtual Network Function) High Availability (HA) on the VeloCloud Edge. When executed, it sets an internal state (conceptually, a non-zero value as indicated by the original description "Non-zero value disregards the vnf instance state for High Availability") which causes the system to disregard the VNF instance's operational state for HA decision-making.

This functionality is typically used during VNF maintenance, upgrades, or troubleshooting scenarios. By suppressing the VNF state's influence on HA, administrators can prevent unwanted HA failovers that might otherwise be triggered by a VNF's transient, known problematic, or intentionally altered state.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --vnf_ha_suppress
```
**Note:** The command itself typically does not produce verbose output upon successful execution, other than potentially returning to the command prompt or a simple confirmation message (not shown in the provided example). The output block shown in the prompt:
```
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
is a generic help/usage message for the `debug.py` script and not the direct output of the `--vnf_ha_suppress` command.

##  Field descriptions
This command is used to modify system behavior and does not return tabular output with specific fields to describe. Its effect is to change how the VeloCloud Edge handles VNF state in relation to its High Availability mechanisms.