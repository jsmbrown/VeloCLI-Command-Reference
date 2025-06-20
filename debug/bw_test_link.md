#	--bw_test_link <logical-id>

##	Description
Retests the bandwidth on a specific WAN link identified by its internal logical ID. This command triggers the VeloCloud Edge to perform a new bandwidth measurement on the designated link. This is useful if a link's performance is suspected to have changed, or after an ISP has made modifications to the link's provisioned capacity, to ensure the Edge has the most accurate data for traffic management. The results of this test are crucial for the Edge's dynamic path selection, traffic steering, and ensuring Quality of Experience (QoE) by providing an up-to-date understanding of the link's capacity.

##  Arguments
| Argument   | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| `logical-id` | **(Required)** The internal logical identifier of the WAN link for which the bandwidth test should be re-initiated. This ID is typically a numerical value assigned by the system to each active WAN interface and can be found using other link diagnostic commands. |

##  Example Usage
The following example shows the output when `debug --bw_test_link` is invoked without the required `logical-id` argument. To properly initiate a bandwidth retest, a specific `logical-id` must be provided (e.g., `debug --bw_test_link 1`).

```
example_com:velocli> debug --bw_test_link 00000003-40c8-4ad6-80b1-c50f34726f11
{
  "bw_test": "test in progress"
}
```

##  Field Descriptions
The output shown in the example is a usage message for the `debug.py` script, displayed because the `--bw_test_link` command was called without its mandatory `logical-id` argument. This help message outlines various general options and subcommands available within the `debug.py` utility, rather than specific fields related to a bandwidth test result.

A successful invocation of `debug --bw_test_link <logical-id>` (e.g., `debug --bw_test_link 1`) would typically initiate the bandwidth test in the background. The command might return a brief confirmation message or no immediate console output. The results of the bandwidth test are subsequently updated in the link's status information, which can be monitored through other CLI commands (e.g., commands that display link status or statistics) or via the VeloCloud Orchestrator interface.
