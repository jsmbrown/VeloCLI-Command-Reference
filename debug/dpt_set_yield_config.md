# --dpt_set_yield_config

## Description
This command applies and/or displays the Data Plane (DP) yield configuration on a VeloCloud Edge. The yield configuration determines how data plane processing tasks yield CPU time, which can impact overall system performance, throughput, and responsiveness, especially under high load.

The behavior of the DP yield mechanism is conceptually defined by parameters such as:
*   **Mode**: The strategy for yielding, such as `adaptive`, `legacy`, `linear`, or `log`.
*   **Minimum Yield**: The shortest duration the DP will yield for.
*   **Maximum Yield**: The longest duration the DP will yield for.

These high-level parameters are typically configured via the VeloCloud Orchestrator. Executing the `debug --dpt_set_yield_config` command on the Edge likely triggers the data plane to apply these pre-configured settings or refreshes its current operational parameters based on them. The command's output displays the resulting low-level, operational yield parameters currently in effect.

## Arguments
This command does not take any direct command-line arguments.

## Example Usage
The following example shows the command being invoked and the resulting output, which displays the current low-level DP yield parameters:
```
example_com:velocli> debug --dpt_set_yield_config
{
  "busy_yield_us": 10,
  "idle_yield_map": [
    100,
    83,
    69
  ]
}
```
*(Note: The values in the example output are illustrative and may vary based on the specific Edge model, software version, and configured yield policy.)*

## Field Descriptions
The command output is in JSON format and includes the following fields, representing the low-level operational parameters of the DP yield configuration:

| Field           | Description                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `busy_yield_us` | The yield time in microseconds (µs) that the data plane processing task will use when the system is detected as busy. A smaller value means more aggressive processing with shorter yields.                 |
| `idle_yield_map`| An array of numerical values, typically representing yield times in microseconds (µs), used by the data plane during idle periods. The interpretation and usage of this map can depend on the configured high-level yield `mode` (e.g., `adaptive`, `legacy`, `linear`, `log`). For example, these values might define a sequence of increasing yield times as idleness persists, or parameters for an adaptive yield algorithm during idle states. |