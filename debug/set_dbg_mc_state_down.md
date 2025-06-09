# --set_dbg_mc_state_down [seg-id]

## Description
Sets the Multicast (MC) state to DOWN on the `vce1` interface of the VeloCloud Edge for a specified segment. This command is intended for Multicast testing purposes. The `vce1` interface is an implicit target of this command.

## Arguments
| Argument | Description |
|---|---|
| seg-id   | **Required.** The identifier of the VeloCloud SD-WAN segment for which the Multicast state on the `vce1` interface will be set to DOWN. |

## Example Usage
```
example_com:velocli> debug --set_dbg_mc_state_down 1
```
This command attempts to set the Multicast state to DOWN for segment `1` on the `vce1` interface. Upon successful execution, it may return a confirmation message (e.g., "Successfully set MC state to DOWN for segment 1 on vce1") or no specific output.

## Field Descriptions
This command is used to modify a state on the VeloCloud Edge and does not produce tabular output.