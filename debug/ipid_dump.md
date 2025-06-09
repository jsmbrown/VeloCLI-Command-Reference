#	--ipid_dump [v4 | v6 | all]

##	Description
Dumps the current IP ID (Identification) table. This table is used by the VeloCloud Edge to manage unique identifiers for IP packets, which is particularly important for processes like IP fragmentation and ensuring proper packet handling through the SD-WAN fabric.

##  Arguments (optional)
The command accepts an optional argument to filter the output by IP version.

| Argument        | Description                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `v4`            | Display the IP ID table specifically for IPv4 packets.                                                                                                                   |
| `v6`            | Display fragmentation identification information relevant to IPv6. IPv6 uses a Fragment Extension Header with an Identification field for managing fragmented packets.      |
| `all`           | Display IP ID information for IPv4 and fragmentation identification information for IPv6.                                                                                |
| (no argument)   | If no argument is specified, the command attempts to dump the IP ID table. The provided example shows an error in this case, which might indicate an argument is implicitly required or there was an internal issue during execution. |

##  Example usage
```
example_com:velocli> debug --ipid_dump
RPC error:  Error calling remote procedure: Internal error
```

##  Field descriptions
The example provided resulted in an error, so no specific output fields can be described. A successful execution of this command would typically display entries from the IP ID table(s), which might include details such as:
*   Source IP Address
*   Destination IP Address
*   Protocol
*   Current IP ID value (for IPv4) or Fragmentation ID (for IPv6)
*   Other relevant state information for managing packet identification.