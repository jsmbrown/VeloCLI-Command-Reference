# `debug --stale_td_dump`

## Description
Displays a list of stale Tunnel Descriptors (TDs). A Tunnel Descriptor is an internal data structure representing a VeloCloud SD-WAN tunnel. Stale TDs are those that are no longer considered active or valid by the system but may not have been fully cleaned up or removed. This command is useful for diagnosing potential issues related to tunnel lifecycle management and resource allocation on the VeloCloud Edge.

## Arguments
This command takes no arguments.

## Example Usage
```
example_com:velocli> debug --stale_td_dump
TD   PI  PEER IP  PEER TYPE  VERSION  STATE  PHY INTF NAME  REF OBJS  DURATION

example_com:velocli>
```

## Field Descriptions
| Column          | Description                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------|
| `TD`            | Tunnel Descriptor ID. A unique identifier assigned to the tunnel instance.                                   |
| `PI`            | Path Identifier. A unique identifier for a specific path associated with the tunnel.                         |
| `PEER IP`       | The IP address of the peer device (e.g., VeloCloud Edge, VeloCloud Gateway) at the remote end of the tunnel. |
| `PEER TYPE`     | The type of the peer device (e.g., EDGE, GATEWAY).                                                         |
| `VERSION`       | The version of the VeloCloud Management Protocol (VCMP) or other relevant protocol used for the tunnel.    |
| `STATE`         | The current state of the Tunnel Descriptor, which for this command output will typically indicate it is "stale". |
| `PHY INTF NAME` | The name of the physical WAN interface on the local Edge that was used for this tunnel path.                 |
| `REF OBJS`      | Reference Objects. Indicates the number of internal system objects (e.g., flows, routes) that might still be referencing this stale Tunnel Descriptor. |
| `DURATION`      | The length of time the Tunnel Descriptor has been in the stale state.                                        |