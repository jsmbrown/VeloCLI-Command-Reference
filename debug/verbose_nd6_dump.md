# --verbose_nd6_dump [Number of entries]

## Description
This command dumps the Neighbor Discovery Protocol (NDP) cache for IPv6 (ND6) for active interfaces on the VeloCloud Edge. The ND6 cache stores information about IPv6 neighbors, such as their link-layer addresses, which is essential for IPv6 communication over the local link. This information is used to resolve IPv6 addresses to MAC addresses, discover routers, and maintain reachability information for neighboring nodes.

## Arguments
| Argument            | Description                                                                                                |
|---------------------|------------------------------------------------------------------------------------------------------------|
| `[Number of entries]` | (Optional) Specifies the maximum number of ND6 cache entries to display per interface. If this argument is omitted, the command typically displays all entries for each active interface. |

## Example usage
```json
example_com:velocli> debug --verbose_nd6_dump
[
  {
    "cache_entry": [],
    "interface": "GE1",
    "snmp_index": 16777216
  }
]
```

## Field descriptions
The command output is a JSON array, where each object represents an active interface and its ND6 cache information.

| Field         | Description                                                                                                                                                                                                                            |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cache_entry` | An array containing details of individual ND6 cache entries for the interface. Each entry typically includes information like the neighbor's IPv6 address, its link-layer (MAC) address, state (e.g., STALE, REACHABLE), and potentially flags or timers. In the provided example, this array is empty, indicating no ND6 entries were present or displayed for this interface at the time of the command execution. |
| `interface`   | The logical name of the network interface on the VeloCloud Edge (e.g., `GE1`) for which the ND6 cache information is being displayed.                                                                                                    |
| `snmp_index`  | The SNMP (Simple Network Management Protocol) interface index (ifIndex). This is a unique positive integer that identifies this network interface for SNMP management purposes, allowing correlation with other SNMP data if needed.      |