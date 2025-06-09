#	`--set_dbg_mc_state_up [seg-id]`

##	Description
This command is used to manually set the Multicast (MC) state to UP on a VeloCloud Edge interface (typically `vce1` or an equivalent interface within the specified segment) for multicast testing purposes. This allows administrators or testers to simulate an active multicast upstream state.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `seg-id` | Specifies the segment ID for which the MC state should be set to UP. If this argument is omitted, the command may apply to a default segment or a globally relevant MC state component associated with an interface like `vce1`. |

##  Example usage
The following example demonstrates how to execute the command. Note that specific output is not provided in the example, but typically, such commands might return a confirmation message or no output upon success.
```
example_com:velocli> debug --set_dbg_mc_state_up
```
If a specific segment ID (e.g., 1) is targeted:
```
example_com:velocli> debug --set_dbg_mc_state_up 1
```

##  Field descriptions
This command is primarily used to change a state and may not produce tabular output.
*   **Confirmation Message:** Upon successful execution, the command may return a simple confirmation message (e.g., "MC state set to UP for segment X") or no output if the operation was successful.
*   **Error Message:** If the command fails (e.g., invalid `seg-id`, internal error), an error message describing the issue will be displayed.