# `--port_groups`

## Description
Displays the list of port groups configured on the VeloCloud Orchestrator (VCO). Port groups are collections of L4 port numbers (e.g., TCP/UDP ports) that can be used in policies for traffic identification and control on VeloCloud Edges.

## Arguments (optional)
This command takes no arguments.

## Example usage
```
example_com:velocli> debug --port_groups
[
  {
    "logicalId": "98b4beff-821d-49f7-89dc-e4450e204d1c",
    "ports": [
      {
        "code_high": 255,
        "code_low": 0,
        "protocol": 0
      },
      {
        "code_high": 80,
        "code_low": 80,
        "protocol": 6
      }
    ],
    "name": "Web Browsing Ports",
    "description": "Standard ports used for web browsing (HTTP/HTTPS)"
  },
  {
    "logicalId": "a1b2c3d4-e5f6-7890-1234-567890abcdef",
    "ports": [
      {
        "code_high": 5060,
        "code_low": 5060,
        "protocol": 17
      },
      {
        "code_high": 5061,
        "code_low": 5061,
        "protocol": 6
      }
    ],
    "name": "VoIP SIP Ports",
    "description": "Standard ports for SIP signaling"
  }
]
```
*(Note: The example output has been expanded for illustrative purposes based on typical port group configurations, as the provided snippet was partial.)*

## Field descriptions
The output is a JSON array, where each object represents a configured port group.

| Field Path             | Description                                                                                                                               |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `[].logicalId`         | A unique identifier string for the port group, assigned by the VeloCloud Orchestrator.                                                    |
| `[].name`              | The user-defined name for the port group (e.g., "Web Browsing Ports").                                                                    |
| `[].description`       | An optional description for the port group.                                                                                               |
| `[].ports`             | An array of objects, where each object defines a specific port or range of ports, and the associated protocol, included in this group.    |
| `[].ports[].code_low`  | The lower bound of the port range (e.g., for a range 80-88, `code_low` would be 80). For a single port, `code_low` equals `code_high`.     |
| `[].ports[].code_high` | The upper bound of the port range (e.g., for a range 80-88, `code_high` would be 88). For a single port, `code_high` equals `code_low`.   |
| `[].ports[].protocol`  | The IP protocol number associated with the port(s). Common values include `6` for TCP, `17` for UDP, or `0` for any protocol.             |