#	--flow_set_idps_state [flow-id] [allow | block]

##	Description
This command allows an administrator to manually set the Intrusion Detection and Prevention System (IDPS) state for a specific network flow, identified by its `[flow-id]`. The state can be configured to either `allow`, which permits the flow through the IDPS, or `block`, which denies the flow. This is useful for immediate manual intervention in traffic handling by the IDPS.

##  Arguments
| Argument    | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| `[flow-id]` | The unique identifier of the network flow whose IDPS state is to be modified. This is the first argument supplied after the command. |
| `allow`     | A literal keyword. When specified as the second argument, it sets the IDPS state for the flow to 'allow', permitting the traffic. |
| `block`     | A literal keyword. When specified as the second argument, it sets the IDPS state for the flow to 'block', denying the traffic.   |

##  Example usage
To set the IDPS state to 'allow' for a flow with ID `12345`:
```
example_com:velocli> debug --flow_set_idps_state 12345 allow
Successfully set IDPS state for flow 12345 to allow.
```

To set the IDPS state to 'block' for a flow with ID `67890`:
```
example_com:velocli> debug --flow_set_idps_state 67890 block
Successfully set IDPS state for flow 67890 to block.
```
*(Note: The exact confirmation message may vary.)*

##  Field descriptions
This command is used to modify the IDPS operational state for a specific flow and does not produce tabular output. A confirmation message indicating the success or failure of the operation is typically displayed on the console.