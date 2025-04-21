#	--app_chat_stats [app id]

##	Description
Displays throughput and flow statistics for a specific application

##  Arguments (optional)
| Argument | Description |
|---|---|
| [app id] | Numerical ID for a specific application defined in the app map.  List can be obtained via the [debug --applications](https://github.com/el-hoffer/VeloCLI-Command-Reference/blob/main/debug/applications.md) command |

##  Example usage
```
example_com:velocli> debug --app_chat_stats 767
[
  {
    "VcoBytesRx": 3479,
    "VcoBytesTx": 1289,
    "VcoPacketsRx": 5,
    "VcoPacketsTx": 8,
    "VcoTcpRetransmits": 0,
    "VcoTcpRttMs": 0,
    "appClass": 7,
    "appClassString": "APP_CLASS_FILE_SHARING",
    "application": 767,
    "applicationString": "APP_BOX_NET",
    "bizRuleId": "38f0dd30-43f8-405e-91da-eb5cd6d009c5",
    "collectorCommonBitmap": -1,
    "collectorLsBitmap": -1,
    "endpoints": {
      "application": 767,
      "innerHostName": "",
      "innerIp": "10.1.1.165",
      "innerMac": "90:6c:ac:01:ca:80",
      "nextHopIp": "192.168.1.1",
      "outerHostName": "client-log.box.com",
      "outerIp": "74.112.186.157",
      "outerPort": 443,
      "segmentId": 0
    },
    "flowCount": 1,
    "flowId": 2613,
    "flowIpTos": 0,
    "flowPath": "Edge2CloudDirect",
    "fwRuleId": "QHT05YvMRyOKdoAyrabAbw",
    "gatewayIp": "",
    "links": [
      {
        "VcoBytesRx": 0,
        "VcoBytesTx": 0,
        "VcoPacketsRx": 0,
        "VcoPacketsTx": 0,
        "bytesRx": 3479,
        "bytesTx": 1289,
        "internalId": "00000005-b421-4c48-b3b5-6e0a06795904",
        "logicalId": "fc:12:63:2e:cb:ed:0000",
        "packetsReplicatedRx": 0,
        "packetsReplicatedTx": 0,
        "packetsRetransTx": 0,
        "packetsRx": 5,
        "packetsTx": 8
      }
    ],
    "netflow": {
      "bytesRx": 3479,
      "bytesTx": 1289,
      "packetsLostRx": 0,
      "packetsReplicatedRx": 0,
      "packetsReplicatedTx": 0,
      "packetsRetransTx": 0,
      "packetsRx": 5,
      "packetsTx": 8,
      "tcpRetransmits": 0,
      "tcpRttMs": 101
    },
    "network": 6,
    "refCount": 1,
    "transport": 6
  }
]

```
