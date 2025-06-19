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
    "cache_entry": [
      {
        "addr": "fe80::f99a",
        "age": 23,
        "ctag": 0,
        "icmp_count": 0,
        "in_progress": "FALSE",
        "is_router": "TRUE",
        "last_nd_pkt_rcvd_time": 1134438180,
        "last_pkt_rcv": 18,
        "last_state_update_time": 1134433171,
        "mac": "54:83:3a:7c:f9:9a",
        "refcnt": 2,
        "stag": 0,
        "state": "REACHABLE"
      }
    ],
    "interface": "GE6",
    "snmp_index": 16777222
  }
]
```

## Field descriptions
| Field         | Description                                                                                                                                                                                                                            |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cache_entry` | An array containing details of individual ND6 cache entries for the interface. |
| `cache_entry.addr` | IPv6 address of the neighbor entry. |
| `cache_entry.age` | Age in seconds of the neighbor entry. |
| `cache_entry.ctag` | VLAN ID on which the neighbor was discovered (`0` if no 802.1Q tag).  |
| `cache_entry.icmp_count` | Number of ICMPv6 messages exchanged with this neighbor. |
| `cache_entry.in_progress` | `true`/`false` indicator of whether discovery process is currently in progress. |
| `cache_entry.is_router` | `true`/`false` indicator of whether the neighbor has been identified as a router via a router advertisement message. |
| `cache_entry.last_nd_pkt_rcvd_time` | Time last neighbor discovery packet was received. |
| `cache_entry.last_pkt_rcv` | Time since the last packet was received from the neighbor. |
| `cache_entry.last_state_update_time` | Time of the most recent neighbor state change. |
| `cache_entry.mac` | MAC address of the neighbor. |
| `cache_entry.refcnt` | Reference count. |
| `cache_entry.stag` | S-Tag on which the neighbor was discovered (`0` if no 802.1ad tag) |
| `cache_entry.state` | Neighbor discovery status (i.e. `Incomplete`, `Reachable`, `Stale`, `Delay`, or `Probe`) |
| `interface`   | The logical name of the network interface on the VeloCloud Edge (e.g., `GE1`) for which the ND6 cache information is being displayed.                                                                                                    |
| `snmp_index`  | The SNMP (Simple Network Management Protocol) interface index (ifIndex). This is a unique positive integer that identifies this network interface for SNMP management purposes, allowing correlation with other SNMP data if needed.      |