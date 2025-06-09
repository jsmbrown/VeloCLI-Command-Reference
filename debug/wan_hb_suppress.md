# debug --wan_hb_suppress [value]

## Description
Manages the suppression of WAN interface heartbeats on a VeloCloud Edge. These heartbeats are essential for the proper functioning of High Availability (HA) features. Disabling these heartbeats by suppressing them can negatively impact HA operations and is **not recommended**.

The command allows an administrator to enable, disable, or check the status of WAN heartbeat suppression. A non-zero value for the argument suppresses the heartbeats, while a value of zero ensures they are active.

## Arguments (optional)
| Argument | Description |
|---|---|
| `value` | (Optional) A numerical input that controls the WAN heartbeat suppression state. <br> - **Non-zero value (e.g., `1`):** Suppresses WAN interface heartbeats. This setting is **not recommended** as it can impair High Availability. <br> - **`0`:** Enables WAN interface heartbeats. This is the default and recommended state for normal HA operation. <br> If the `value` argument is omitted, the command typically displays the current WAN heartbeat suppression status. |

## Example usage
To check the current WAN heartbeat suppression status:
```
example_com:velocli> debug --wan_hb_suppress
WAN Heartbeat Suppression: Disabled
```

To suppress WAN interface heartbeats (e.g., by setting `value` to `1` - **Not Recommended**):
```
example_com:velocli> debug --wan_hb_suppress 1
WAN Heartbeat Suppression has been set to: Enabled
```

To ensure WAN interface heartbeats are enabled (e.g., by setting `value` to `0` - Recommended):
```
example_com:velocli> debug --wan_hb_suppress 0
WAN Heartbeat Suppression has been set to: Disabled
```

## Field descriptions
The output of this command is typically a single line of text confirming the action taken or displaying the current status. It does not produce tabular output with multiple fields.

| Output Element | Description |
|---|---|
| Status Message | A confirmation message indicating the new state of WAN heartbeat suppression (e.g., `WAN Heartbeat Suppression has been set to: Enabled`) or the current status if no value was provided (e.g., `WAN Heartbeat Suppression: Disabled`). |