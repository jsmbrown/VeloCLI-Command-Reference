# `--sub_path_stats [all | peer-id]`

## Description
Displays current statistics for sub-paths. Sub-paths are the individual WAN link contributions that form the overlay tunnels (paths) to peer VeloCloud Edges or Gateways. This command provides detailed performance metrics for these underlying transport connections, including latency, jitter, loss, throughput, and Quality of Experience (QoE) data.

## Arguments (optional)
| Argument  | Description                                                                                                                               |
| :-------- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| `all`     | (Default if no argument is specified) Displays sub-path statistics for all active peer connections (i.e., to all other Edges or Gateways). |
| `peer-id` | Specifies the identifier of a peer (Edge or Gateway) for which to display sub-path statistics. This could be a system-assigned ID or a configured name. |

## Example usage
The command output is in JSON format.

**Example when no paths are found:**
```json
example_com:velocli> debug --sub_path_stats
{
  "Error": "No Paths Found"
}
```

**Hypothetical example of a successful output (e.g., with `all` or default argument):**
*The following is a conceptual representation, as the actual field names and structure might vary.*
```json
example_com:velocli> debug --sub_path_stats
[
  {
    "peerId": "3294602a-5a69-4694-a7d2-811aff737faa",
    "peerName": "Hub-Edge-01",
    "subPaths": [
      {
        "subPathId": "LINK1002-P1-S0-L0",
        "wanLink": "Public Wired 1 (GE1)",
        "localIp": "192.168.100.10",
        "remoteIp": "203.0.113.50",
        "transportProtocol": "UDP",
        "state": "STABLE",
        "latencyMs": 12.5,
        "jitterMs": 1.8,
        "lossPercent": 0.01,
        "txThroughputBps": 15000000,
        "rxThroughputBps": 10000000,
        "qoeScore": 9.8,
        "decActive": true,
        "packetsTx": 1203948,
        "packetsRx": 1038749,
        "bytesTx": 1500000000,
        "bytesRx": 980000000
      },
      {
        "subPathId": "LINK1003-P1-S0-L1",
        "wanLink": "LTE Backup (USB1)",
        "localIp": "192.168.101.10",
        "remoteIp": "203.0.113.51",
        "transportProtocol": "UDP",
        "state": "STABLE_POOR_PERF",
        "latencyMs": 85.2,
        "jitterMs": 15.1,
        "lossPercent": 0.5,
        "txThroughputBps": 2000000,
        "rxThroughputBps": 1000000,
        "qoeScore": 6.5,
        "decActive": true,
        "packetsTx": 50123,
        "packetsRx": 45876,
        "bytesTx": 60000000,
        "bytesRx": 40000000
      }
    ]
  },
  {
    "peerId": "891413b5-4fd7-417f-8efc-102aeb579df8",
    "peerName": "Branch-Edge-77",
    "subPaths": [
      {
        "subPathId": "LINK2005-P1-S0-L0",
        "wanLink": "Business Broadband (GE2)",
        "localIp": "198.51.100.20",
        "remoteIp": "192.0.2.100",
        "transportProtocol": "UDP",
        "state": "UNSTABLE",
        "latencyMs": 30.1,
        "jitterMs": 22.5,
        "lossPercent": 1.2,
        "txThroughputBps": 5000000,
        "rxThroughputBps": 3000000,
        "qoeScore": 5.1,
        "decActive": false,
        "packetsTx": 98765,
        "packetsRx": 87654,
        "bytesTx": 120000000,
        "bytesRx": 90000000
      }
    ]
  }
]
```

## Field descriptions
The output is in JSON format.
*   If `all` is specified or no argument is given, the output is an array of peer objects.
*   If a specific `peer-id` is provided, the output is typically a single peer object (not nested in an array).

Note that the exact set of fields and their names might vary slightly based on the Edge software version and specific VeloCloud platform.

**Error Field (if applicable):**
This field appears at the top level of the JSON response if an error occurs.

| Field (JSON Key) | Description                                                                                                |
| :--------------- | :--------------------------------------------------------------------------------------------------------- |
| `Error`          | (String) If present, indicates an error occurred (e.g., "No Paths Found", "Invalid peer-id", "Peer offline"). |

**Fields for each Peer Object (present in the array if `all`/default, or as the root object if `peer-id` is specified):**

| Field (JSON Key) | Description                                                                          |
| :--------------- | :----------------------------------------------------------------------------------- |
| `peerId`         | (String) The unique identifier of the peer VeloCloud device (Edge or Gateway).       |
| `peerName`       | (String) The configured name of the peer device.                                     |
| `subPaths`       | (Array of Objects) A list containing statistics for each sub-path to this peer.      |

**Fields within each `subPaths` Array Object:**
These fields describe the characteristics and performance of an individual sub-path (WAN link contribution to a tunnel).

| Field (JSON Key)    | Description                                                                                                                                                           |
| :------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `subPathId`         | (String) A unique identifier for the specific sub-path. This often includes internal system information about the link, path, session, and leg.                       |
| `wanLink`           | (String) The name or identifier of the local WAN interface (e.g., "GE1", "Public Wired 1", "LTE0") used for this sub-path.                                            |
| `localIp`           | (String) The local IP address used for this sub-path.                                                                                                                 |
| `remoteIp`          | (String) The remote IP address of the peer for this sub-path.                                                                                                         |
| `transportProtocol` | (String) The transport protocol used for the tunnel over this sub-path (e.g., "UDP", "TCP"). VeloCloud primarily uses UDP for its proprietary VCRP tunnels.             |
| `state`             | (String) The current operational state of the sub-path (e.g., "UP", "DOWN", "STABLE", "UNSTABLE", "DEGRADED", "STALE", "STABLE_POOR_PERF", "INIT", "NEGOTIATING").     |
| `latencyMs`         | (Number) The measured round-trip latency on the sub-path in milliseconds. This is a key metric for QoE.                                                               |
| `jitterMs`          | (Number) The measured jitter (variation in packet delay) on the sub-path in milliseconds. High jitter negatively impacts real-time applications like voice and video. |
| `lossPercent`       | (Number) The measured packet loss on the sub-path as a percentage.                                                                                                    |
| `txThroughputBps`   | (Number) The current transmit throughput (actual data rate sent) on the sub-path in bits per second.                                                                  |
| `rxThroughputBps`   | (Number) The current receive throughput (actual data rate received) on the sub-path in bits per second.                                                               |
| `qoeScore`          | (Number) An overall Quality of Experience (QoE) score for this sub-path, typically on a scale (e.g., 0-10). This score is dynamically calculated based on latency, jitter, and loss. |
| `decActive`         | (Boolean) Indicates if Dynamic Error Correction (DEC) techniques, such as Forward Error Correction (FEC) or packet duplication, are currently active on this sub-path to mitigate packet loss or jitter. |
| `bwMeasuredKbps`    | (Number, Optional) Measured available bandwidth on this sub-path in kilobits per second. This might be derived from active or passive monitoring.                     |
| `bwUtilPct`         | (Number, Optional) Current bandwidth utilization percentage for this sub-path, calculated against its configured or measured capacity.                                |
| `packetsTx`         | (Number) Total packets transmitted on this sub-path since the last counter reset or path establishment.                                                               |
| `packetsRx`         | (Number) Total packets received on this sub-path since the last counter reset or path establishment.                                                                |
| `bytesTx`           | (Number) Total bytes transmitted on this sub-path since the last counter reset or path establishment.                                                                 |
| `bytesRx`           | (Number) Total bytes received on this sub-path since the last counter reset or path establishment.                                                                  |
| `uptimeSecs`        | (Number, Optional) Duration in seconds that this sub-path has been in its current stable state or active.                                                             |
| `reason`            | (String, Optional) If the sub-path is not in an ideal state (e.g., "DOWN", "UNSTABLE"), this field may provide a reason code or description.                         |