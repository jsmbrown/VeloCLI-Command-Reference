#	--control_bytes &lt;peer | link&gt; [clear | all]

##	Description
Dumps the number of transmitted (tx) and received (rx) bytes and packets/messages for control messages, categorized by each peer or link. Control messages are part of the VeloCloud Management Protocol (VCMP) and VeloCloud Routing Protocol (VCRP) used for communication between Edges, Gateways, and the Orchestrator. These statistics are useful for monitoring the health and volume of control plane traffic on the VeloCloud Edge.

The command can also be used to clear these statistics.

##  Arguments
| Argument | Description |
|---|---|
| `<peer | link>` (mandatory first argument) | Specifies the scope for which control message statistics should be actioned. <br> - `peer`: The operation (display or clear) applies to control messages exchanged with peer VeloCloud devices (i.e., other Edges or Gateways). <br> - `link`: The operation (display or clear) applies to control messages exchanged over the Edge's specific WAN links. |
| `clear` (optional second argument) | If specified, the command will reset the control message counters for the chosen scope (`peer` or `link`) to zero. |
| `all` (optional second argument) | If specified, or if this second argument is omitted, the command will display the current control message counters for the chosen scope (`peer` or `link`). This is the default action. |

##  Example usage
The command requires at least the scope (`peer` or `link`) to be specified.

```
# Attempting to run the command without specifying 'peer' or 'link' results in an error:
example_com:velocli> debug --control_bytes
Insufficient Arguments;  Please choose 'peer' or 'link'

# To display control byte statistics per peer (default action):
example_com:velocli> debug --control_bytes peer
Peer ID             TX Bytes    TX Packets    RX Bytes    RX Packets
--------------------------------------------------------------------
gateway-1           10240       100           20480       200
edge-2              5120        50            15360       150
# (Output format is illustrative as no successful example was provided in the input)

# To explicitly display control byte statistics per link using 'all':
example_com:velocli> debug --control_bytes link all
Link ID (Interface) TX Bytes    TX Packets    RX Bytes    RX Packets
--------------------------------------------------------------------
GE1                 8192        80            18432       180
GE2                 7168        70            17408       170
# (Output format is illustrative)

# To clear control byte statistics per peer:
example_com:velocli> debug --control_bytes peer clear
# (This command would typically not produce output, or might show a simple confirmation message)

# To clear control byte statistics per link:
example_com:velocli> debug --control_bytes link clear
# (No output or confirmation)
```

##  Field descriptions
When displaying statistics (e.g., `debug --control_bytes peer` or `debug --control_bytes link all`), the output would typically include the following fields:

| Column | Description |
|---|---|
| Peer ID / Link ID | Identifier for the peer (e.g., name or system ID of another VeloCloud Edge or Gateway) or the local WAN link (e.g., interface name like GE1, GE2, or a system-internal link identifier). |
| TX Bytes | Total number of control message bytes transmitted to the peer or over the link since the last counter reset or device reboot. |
| TX Packets | Total number of control message packets (or messages) transmitted to the peer or over the link since the last counter reset or device reboot. |
| RX Bytes | Total number of control message bytes received from the peer or over the link since the last counter reset or device reboot. |
| RX Packets | Total number of control message packets (or messages) received from the peer or over the link since the last counter reset or device reboot. |