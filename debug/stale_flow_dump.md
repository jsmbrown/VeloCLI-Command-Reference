#	--stale_flow_dump [all | dest-ip]

##	Description
This command dumps the current stale flow table entries from the VeloCloud Edge's flow cache. Stale flows are those that have not seen traffic for a certain period and are candidates for removal from the active flow table. This information is useful for troubleshooting issues related to traffic flow, resource utilization, or unexpected connection behavior.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays all stale flow entries. This is the default behavior if no argument is specified. |
| `dest-ip` | Filters the output to show only stale flow entries destined for the specified IP address. You would replace `dest-ip` with the actual destination IP address (e.g., `192.168.1.100`). |

##  Example usage
```
example_com:velocli> debug --stale_flow_dump
PTR   FC_ID  SIP  DIP  SPORT  DPORT  DSCP  DEAD SINCE  REF OBJS  RTQ PKTS

```
To filter by a specific destination IP:
```
example_com:velocli> debug --stale_flow_dump 10.0.0.5
PTR   FC_ID  SIP  DIP  SPORT  DPORT  DSCP  DEAD SINCE  REF OBJS  RTQ PKTS
(Output would show flows destined to 10.0.0.5)
```

##  Field descriptions
| Column | Description |
|---|---|
| `PTR` | Pointer or internal identifier for the flow entry. |
| `FC_ID` | Flow Cache Identifier, a unique ID for the flow within the cache. |
| `SIP` | Source IP Address of the flow. |
| `DIP` | Destination IP Address of the flow. |
| `SPORT` | Source Port number of the flow. |
| `DPORT` | Destination Port number of the flow. |
| `DSCP` | Differentiated Services Code Point value associated with the flow, indicating its Quality of Service (QoS) marking. |
| `DEAD SINCE` | Timestamp or duration indicating how long the flow has been considered stale or inactive. |
| `REF OBJS` | Number of referenced objects associated with this flow entry. |
| `RTQ PKTS` | Number of packets in the retransmit queue for this flow, potentially indicating issues with packet delivery or acknowledgement. |