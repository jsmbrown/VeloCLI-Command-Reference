#	--nvs_lb_table

##	Description
Displays the Non-VeloCloud Site (NVS) Load Balancing (LB) table. This table provides information about how traffic destined for NVS (also known as Non-SD-WAN Destinations or NSDs) is distributed across available paths or interfaces. This is particularly relevant when multiple tunnels or paths are established to an NVS.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```json
example_com:velocli> debug --nvs_lb_table
[
  {
    "dcLogicalIdIdx": 65535,
    "ifaceIdxArray": [],
    "numPaths": 0,
    "nvsLogicalId": "07edf3ce-bc52-4087-9faf-c4b96f9c4571"
  }
]
```

##  Field descriptions
| Field | Description |
|---|---|
| `dcLogicalIdIdx` | Index of the logical ID. A value of 65535 often indicates a default, wildcard, or "not applicable" value. In the context of NVS load balancing, this might refer to a specific VeloCloud Gateway or Hub Edge through which the NVS is reached, or it could indicate that the load balancing decision is not tied to a specific data center construct. |
| `ifaceIdxArray` | An array of interface indexes that are part of the load balancing group for this NVS. An empty array `[]` indicates that no specific interfaces are currently assigned or active for load balancing to this NVS, or that path-based load balancing is used instead of interface-based. |
| `numPaths` | The number of active paths currently available and considered for load balancing traffic to this NVS. A value of `0` indicates no active paths are currently established or eligible for load balancing to this specific NVS. |
| `nvsLogicalId` | The unique logical identifier (UUID) of the Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD). This ID uniquely identifies the external site to which load balancing rules apply. |