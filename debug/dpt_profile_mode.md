# --dpt_profile_mode [precise|imprecise]

## Description
The `debug --dpt_profile_mode` command is used to control the profiling mode for Data Plane (DP) tasks on the VeloCloud Edge. Profiling allows administrators to gather performance data for these tasks, which is essential for diagnosing and troubleshooting performance-related issues within the VeloCloud SD-WAN dataplane.

Two profiling modes can be specified using this command:
-   **Precise Profiling**: Activated by providing the `precise` argument. This mode enables the collection of highly detailed performance metrics for DP tasks. While extremely useful for in-depth analysis and debugging complex performance issues, precise profiling may introduce a minor performance overhead on the Edge due to the increased granularity of data collection.
-   **Imprecise Profiling**: Activated by providing the `imprecise` argument. This mode uses less resource-intensive profiling techniques, offering general performance data with minimal impact on the Edge's system resources. If precise profiling was active, using `imprecise` would typically disable it or revert to a default, less detailed profiling level.

If the command is invoked without any arguments (e.g., `debug --dpt_profile_mode`), it is generally expected to display the current profiling mode active on the Edge.

## Arguments
| Argument    | Description                                                                                                                               |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `precise`   | Optional. Sets the Data Plane task profiling mode to `precise`, enabling detailed performance metric collection.                            |
| `imprecise` | Optional. Sets the Data Plane task profiling mode to `imprecise`. This typically disables `precise` mode if it was previously active, or sets a general, less detailed profiling level. |
| _none_      | If no argument is provided, the command is expected to display the current profiling mode for Data Plane tasks.                             |

## Example Usage
The provided example demonstrates invoking the command. This is often used to check the current profiling mode:
```
example_com:velocli> debug --dpt_profile_mode
```
*(Note: The specific output for this command invocation was not provided in the input materials. It would typically display the current profiling mode, for example: "Current profiling mode: imprecise".)*

To explicitly set the profiling mode, you would specify either `precise` or `imprecise` as an argument:

To enable precise profiling:
```
example_com:velocli> debug --dpt_profile_mode precise
```
*(This action would typically result in a confirmation message, such as "Profiling mode set to precise.", or provide no output if the command executes successfully.)*

To enable imprecise profiling (or disable precise profiling):
```
example_com:velocli> debug --dpt_profile_mode imprecise
```
*(Similarly, this action would typically result in a confirmation message, such as "Profiling mode set to imprecise.", or provide no output on success.)*

## Field Descriptions
This command does not produce tabular output with multiple columns and rows (unlike commands such as `debug --routes`).
-   When querying the current mode (i.e., when invoked without arguments), the output is expected to be a single line of text indicating the active profiling state (e.g., `Current profiling mode: precise`).
-   When setting a new mode (i.e., when invoked with the `precise` or `imprecise` argument), the output is typically a confirmation message indicating the successful change of mode, or no output if the command is successful.