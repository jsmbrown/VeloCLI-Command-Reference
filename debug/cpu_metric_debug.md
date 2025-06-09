# --cpu_metric_debug [reset | set <N>]

## Description
Provides debugging capabilities for CPU metrics related to health statistics on the VeloCloud Edge. This command can display current CPU-related metrics or be used to simulate specific CPU load conditions for testing purposes by resetting or setting a CPU metric value.
When run without parameters, it displays the current CPU metric debug information.
When `reset` is used, it resets the CPU value.
When `set <N>` is used, it sets the CPU value to `N` for testing health statistics.
**Note:** This command is unavailable in GA (General Availability) builds.

## Arguments (optional)
The command can be run with the following optional parameters:

| Parameter | Description |
|---|---|
| `reset` | Resets the CPU metric value used for health statistics to its default. |
| `set <N>` | Sets the CPU metric value to `<N>` for testing health statistics. Replace `<N>` with the desired numerical value. This allows simulating specific CPU load conditions. |
| *none* | If no parameter is provided, the command displays the current CPU metric debug information, as shown in the example below. |

## Example usage
The following example demonstrates the command executed without any parameters, displaying the current CPU metric debug information:
```
example_com:velocli> debug --cpu_metric_debug
{
  "active_flow_count": 142,
  "flow_count": 142,
  "handoffq_drops": 0,
  "link_health": [],
  "nvs": [
}
```

## Field descriptions
The output is in JSON format. The key fields are described below:

| Field | Description |
|---|---|
| `active_flow_count` | The current number of active data flows being processed by the VeloCloud Edge. |
| `flow_count` | The total number of data flows (both active and recently inactive) known to the Edge. |
| `handoffq_drops` | The number of packets dropped from the handoff queue. The handoff queue is an internal buffer used for passing packets between different processing components within the Edge; drops here can indicate internal congestion or an inability to process packets at the incoming rate. |
| `link_health` | An array that would typically contain health status information for the Edge's WAN links. This can include metrics such as latency, jitter, packet loss, and bandwidth utilization. In the provided example, this array is empty, indicating either no links are being reported or the output is truncated. |
| `nvs` | An array that would typically contain information related to Non-VeloCloud Sites (NVS) or Non-SD-WAN Destinations (NSD). This includes details about IPSec or GRE tunnels to these non-SD-WAN endpoints. In the provided example, the array is shown as empty or truncated. |