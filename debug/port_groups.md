#	--port_groups

##	Description
Dump the list of port groups configured on the VeloCloud Orchestrator (VCO). Port groups are used to categorize and manage network ports, often for applying consistent policies or configurations.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
```
example_com:velocli> debug --port_groups
[
  {
    "logicalId": "cc3a64e0-781b-4aa2-b02d-b57e1f2be488",
    "ports": [
      {
        "code_high": 255,
        "code_low": 255,
        "port_high": 5061,
        "port_low": 5060,
        "proto": 17,
        "type": 255
      },
      {
        "code_high": 255,
        "code_low": 255,
        "port_high": 5061,
        "port_low": 5060,
        "proto": 6,
        "type": 255
      }
    ]
  }
]

```
##  Field descriptions
The output is a JSON array, where each object represents a configured port group with the following fields:

| Field       | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `logicalId` | A unique identifier (UUID) for the port group.                              |
| `ports`     | An array of objects, where each object defines a specific port or port range within the group. |
| `ports.code_high` | For ICMP based service groups, indicates the high end of the ICMP code range. (value of 255 for non-ICMP based groups) |
| `ports.code_low`  | For ICMP based service groups, indicates the low end of the ICMP code range. (value of 255 for non-ICMP based groups) |
| `ports.port_high`      | For TCP or UDP based groups, indicates high end of the port range. (value of 255 for non-TCP/UDP based groups) |
| `ports.port_low`      | For TCP or UDP based groups, indicates low end of the port range. (value of 255 for non-TCP/UDP based groups) |
| `ports.proto`  | The IP protocol number (e.g., 0 for "Any", 1 for ICMP, 6 for TCP, 17 for UDP). |
| `ports.type`      | For ICMP based service groups, indicates the ICMP message type (i.e. `8` for ICMP Echo, `30` for traceroute, etc.)    |