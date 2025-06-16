#	`--chat_stats` `[sip=<source_ip>]` `[dip=<destination_ip>]` `[dport=<destination_port>]` `[app_id=<application_id>]` `[pretty_file_name=<filename>]`

##	Description
Dumps statistics for current communication sessions, primarily related to VeloCloud Management Protocol (VCMP) exchanges between the VeloCloud Edge and the VeloCloud Orchestrator. Optional filters can be applied to narrow down the scope of the displayed statistics.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `sip=<source_ip>` | Filter statistics by the source IP address of the communication session. |
| `dip=<destination_ip>` | Filter statistics by the destination IP address of the communication session. |
| `dport=<destination_port>` | Filter statistics by the destination port of the communication session. |
| `app_id=<application_id>` | Filter statistics by a specific application ID associated with the communication. |
| `pretty_file_name=<filename>` | Specifies a filename to which the output will be written in a formatted, human-readable (pretty) JSON structure. |

##  Example usage
```
example_com:velocli> debug --chat_stats
[
  {
    "VcoBytesRx": 3604,
    "VcoBytesTx": 3604,
    "VcoPacketsRx": 22,
    "VcoPacketsTx": 22,
    "VcoTcpRetransmits": 0,
    "VcoTcpRttMs": 0,
    "appClass": 13,
    "appClassString": "APP_CLASS_NETWORK_SERVICE",
    "application": 70,
    "applicationString": "APP_ICMP",
    "bizRuleId": "a3217164-4b7e-42a0-a460-275671ceb6b9",
    "collectorCommonBitmap": -1,
    "collectorLsBitmap": -1,
    "endpoints": {
      "application": 70,
      "flowId": 7512169809572895257,
      "innerHostName": "",
      "innerIp": "1.2.3.4",
      "innerMac": "00:00:00:00:00:00",
      "nextHopIp": "0.0.0.0",
      "outerHostName": "",
      "outerIp": "10.10.10.1",
      "outerPort": 2048,
      "segmentId": 1
    },
    "flowCount": 4,
    "flowId": 104985,
    "flowIpTos": 0,
    "flowPath": "Edge2EdgeViaHub",
    "fwRuleId": "",
    "gatewayIp": "",
    "links": [
      {
        "VcoBytesRx": 1414,
        "VcoBytesTx": 1414,
        "VcoPacketsRx": 7,
        "VcoPacketsTx": 7,
        "bytesRx": 0,
        "bytesTx": 0,
        "internalId": "00000001-3913-4132-bca0-dd18bdf45da5",
        "lastPacketOnLinkIsSecure": true,
        "logicalId": "12:34:56:78:9a:bc:0000",
        "packetsReplicatedRx": 0,
        "packetsReplicatedTx": 0,
        "packetsRetransTx": 0,
        "packetsRx": 0,
        "packetsTx": 0,
        "unencryptUserPayloadLinkCfg": false
      }
    ],
    "netflow": {
      "bytesRx": 0,
      "bytesTx": 0,
      "packetsLostRx": 0,
      "packetsReplicatedRx": 0,
      "packetsReplicatedTx": 0,
      "packetsRetransTx": 0,
      "packetsRx": 0,
      "packetsTx": 0,
      "tcpRetransmits": 0,
      "tcpRttMs": 0
    },
    "network": 1,
    "refCount": 5,
    "transport": 1,
    "unencryptUserPayloadFlowCfg": false
  }
]
```
##  Field descriptions
