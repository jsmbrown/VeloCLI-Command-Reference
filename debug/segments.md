#	--segments `[vpn|gateway|controller]`

##	Description
Displays information about configured network segments on the VeloCloud Edge. Network segmentation allows for the isolation of traffic and routing policies within the SD-WAN overlay. This command can be used to view all segments or filter by specific types such as VPN, Gateway, or Controller segments.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `vpn` | Show only VPN segments. These are typically user-defined segments for isolating different types of traffic or tenants. |
| `gateway` | Show only Gateway segments. These segments are often related to connectivity with VeloCloud Gateways. |
| `controller` | Show only Controller segments. These segments are related to management and control plane communication with the VeloCloud Orchestrator. |
| `none` | If no argument is provided, all configured segments are displayed. |

##  Example usage
```
example_com:velocli> debug --segments
{
  "iterator": [
    {
      "id": 0,
      "name": "Global Segment",
      "state": "ALIVE"
    },
    {
      "id": 1,
      "name": "User Segment A",
      "state": "ALIVE"
    }
  ]
}
```

##  Field descriptions
| Column | Description |
|---|---|
| `id` | The numerical identifier for the segment. |
| `name` | The user-defined or system-defined name of the segment. "Global Segment" is a default segment. |
| `state` | The operational state of the segment. "ALIVE" indicates the segment is active and functioning. |