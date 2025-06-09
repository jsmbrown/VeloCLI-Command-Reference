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
    "VcoBytesRx": 4522,
    "VcoBytesTx": 3923,
    "VcoPacketsRx": 23,
    "VcoPacketsTx": 19
  }
]
```
##  Field descriptions
The output is a JSON array, where each object represents a set of statistics for a communication session or an aggregation.
| Field | Description |
|---|---|
| `VcoBytesRx` | The total number of bytes received from the VeloCloud Orchestrator (VCO) for the conversations matching the filter criteria. |
| `VcoBytesTx` | The total number of bytes transmitted to the VeloCloud Orchestrator (VCO) for the conversations matching the filter criteria. |
| `VcoPacketsRx` | The total number of packets received from the VeloCloud Orchestrator (VCO) for the conversations matching the filter criteria. |
| `VcoPacketsTx` | The total number of packets transmitted to the VeloCloud Orchestrator (VCO) for the conversations matching the filter criteria. |