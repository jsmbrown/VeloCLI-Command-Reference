#	--bgp

##	Description
Shows BGP (Border Gateway Protocol) operational data on the VeloCloud Edge. This command provides insights into the current BGP configuration, the status of BGP neighbor adjacencies, and the networks being advertised or received via BGP. BGP is typically used on Edges for dynamic routing with LAN-side devices or for establishing peering with Non-VeloCloud Sites (NVS/NSD).

##  Arguments
This command does not take any arguments.

##  Example usage
```json
example_com:velocli> debug --bgp
[
  {
    "enabled": false,
    "grEnabled": false,
    "holdtime": 180,
    "keepalive": 60,
    "localAS": 65000,
    "routerId": "192.168.12.1",
    "neighbors": [
      {
        "address": "169.254.0.1",
        "remoteAS": 65515,
        "holdTime": 90,
        "keepAlive": 30,
        "state": "Established",
        "defaultOriginate": false,
        "adjRibIn": 0,
        "adjRibOut": 1,
        "upTime": "1d00h03m",
        "prefixCount": 0
      }
    ],
    "networks": [
      {
        "prefix": "192.168.12.0/24"
      }
    ]
  }
]
```

##  Field descriptions
The command output is a JSON array. Each object in the array represents a BGP instance on the Edge (often, there's one BGP instance per configured segment that uses BGP). The fields for each BGP instance are described below:

| Field             | Description                                                                                                |
|-------------------|------------------------------------------------------------------------------------------------------------|
| `enabled`         | (Boolean) Indicates if BGP is enabled for this instance. `true` if enabled, `false` otherwise.             |
| `grEnabled`       | (Boolean) Indicates if BGP Graceful Restart (GR) capability is enabled for this instance. `true` if enabled, `false` otherwise. |
| `holdtime`        | (Integer) The configured BGP hold time in seconds. If the Edge does not receive a keepalive or update message from a neighbor within this period, the BGP session is torn down. |
| `keepalive`       | (Integer) The configured BGP keepalive interval in seconds. Keepalive messages are periodically sent to neighbors to maintain the session. |
| `localAS`         | (Integer) The Autonomous System (AS) number configured for the local VeloCloud Edge for this BGP instance. |
| `routerId`        | (String) The BGP router ID for this BGP instance on the Edge. This is typically an IP address unique within the BGP domain. |
| `neighbors`       | (Array) A list of JSON objects, where each object contains details about a specific BGP neighbor (peer).   |
| `neighbors[].address` | (String) The IP address of the BGP neighbor.                                                              |
| `neighbors[].remoteAS`| (Integer) The Autonomous System (AS) number of the remote BGP neighbor.                                    |
| `neighbors[].holdTime`| (Integer) The negotiated BGP hold time with this specific neighbor in seconds.                             |
| `neighbors[].keepAlive`| (Integer) The negotiated BGP keepalive interval with this specific neighbor in seconds.                      |
| `neighbors[].state`   | (String) The current state of the BGP session with this neighbor (e.g., "Established", "Idle", "Connect", "Active", "OpenSent", "OpenConfirm"). |
| `neighbors[].defaultOriginate` | (Boolean) Indicates if the Edge is configured to advertise a default route (0.0.0.0/0) to this neighbor. `true` if yes, `false` otherwise. |
| `neighbors[].adjRibIn`| (Integer) The number of route prefixes present in the Adjacency-RIB-In from this neighbor. These are routes received from the neighbor *before* any inbound BGP policies or filters are applied. |
| `neighbors[].adjRibOut`| (Integer) The number of route prefixes present in the Adjacency-RIB-Out to this neighbor. These are routes advertised to the neighbor *after* any outbound BGP policies or filters are applied. |
| `neighbors[].upTime`  | (String) The duration for which the BGP session with this neighbor has been in the "Established" state (e.g., "1d00h03m" for 1 day, 0 hours, 3 minutes). |
| `neighbors[].prefixCount`| (Integer) The number of prefixes received from this neighbor that are currently active and installed in the BGP Local RIB (Routing Information Base) after inbound policies have been applied. |
| `networks`        | (Array) A list of JSON objects, where each object represents a network prefix that this BGP instance is configured to advertise into BGP. |
| `networks[].prefix`| (String) The network prefix (e.g., "192.168.12.0/24") being advertised by this BGP instance. This is typically a network connected to the Edge or learned through other routing protocols on the Edge. |