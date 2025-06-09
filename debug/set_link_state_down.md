# --set_link_state_down &lt;interface_logical_name&gt;

## Description
Administratively sets the internal operational state of a specified WAN link on the VeloCloud Edge to DOWN. This command is typically used for diagnostic or testing purposes, such as:
*   Simulating a link failure to observe SD-WAN failover behavior, including how traffic is re-routed over remaining active paths and how Dynamic Multipath Optimization™ (DMPO) adapts.
*   Testing specific policy configurations, for example, how business policies react to link outages or to verify Conditional Backhaul (CBH) functionality.
*   Isolating a potentially problematic link for troubleshooting without needing to physically disconnect cables, allowing for focused diagnostics.

When a link's state is set to DOWN using this command, the VeloCloud Edge will cease to consider it for building tunnels (paths) or for forwarding user traffic. The link status will also be reported as down to the VeloCloud Orchestrator. To bring the link back UP, a corresponding command `debug --set_link_state_up <interface_logical_name>` would typically be used, or the Edge might need a service restart, depending on the software version and specific behavior.

## Arguments
| Argument                 | Description                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| `&lt;interface_logical_name&gt;` | **Required.** The logical identifier of the WAN interface to be set to the DOWN state. Common examples include `GE1`, `GE2`, `SFP1`, `USB1`, etc., corresponding to the physical or virtual ports configured as WAN interfaces on the Edge. The exact names can be found in the Edge's configuration or link status displays. |

## Example Usage
To set the link `GE1` to the DOWN state:
```
example_com:velocli> debug --set_link_state_down GE1
Successfully set link GE1 state to DOWN.
```
*(Note: The exact success message may vary slightly based on the Edge software version.)*

If the command is invoked without specifying the required `&lt;interface_logical_name&gt;` argument, the system will display usage information for the `debug` command, as shown in the provided input:
```
example_com:velocli> debug --set_link_state_down
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
...(output truncated for brevity)
```

## Field Descriptions
| Column | Description |
|---|---|
| N/A    | This command does not produce tabular output. Upon successful execution, it typically returns a confirmation message indicating that the link state has been changed (e.g., "Successfully set link &lt;interface_logical_name&gt; state to DOWN"). If an error occurs (e.g., an invalid interface name is provided or the interface does not exist), an appropriate error message will be displayed. |