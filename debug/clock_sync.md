#	--clock_sync

##	Description
Dumps the current clock synchronization state between the VeloCloud Edge to peers.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --clock_sync
[
  {
    "clockSyncRounds": 5881,
    "clockSyncsRecvd": 50,
    "clockSyncsThisRound": 37,
    "configIntervalMin": -1,
    "csreqtimerHandle": "0x7f92d5e17f00",
    "nodeType": "VCE",
    "offsetUs": -147472614236,
    "peerId": "c8d0a769-1daf-4670-91ad-5b038ea9b4d6",
    "timeoutDeltaMs": -18817,
    "timeoutMs": 762955352
  }
]
```

##  Field descriptions
| Field                 | Description                                                                                                |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| `clockSyncRounds`     | The total number of clock synchronization rounds that have occurred since the Edge started.                |
| `clockSyncsRecvd`     | The total number of clock synchronization messages (responses) received by the Edge in the previous round.  Each round consists of 50 requests to calculate drift.                     |
| `clockSyncsThisRound` | The number of clock synchronization messages received in the current synchronization round.                |
| `configIntervalMin`   | The configured minimum interval (in minutes) for clock synchronization. Default value is 30 minutes. |
| `csreqtimerHandle`    | Timer handle ID.                 |
| `nodeType`   | Edge role of `VCE` when peer is a gateway or `DCE_CLIENT` when peer is an edge.                             |
| `offsetUs`  | Time offset between edge and peer in microseconds                                 |
| `peerId`   | Logical ID of the peer edge or gateway.                                      |
| `timeoutDeltaMs`         | Timeout delta                                                                    |
| `timeoutMs`       | Time remaining in until clock sync is re-run.                                                          |