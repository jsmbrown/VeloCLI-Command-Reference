#	--jitter

##	Description
Displays the current table of flows for which the jitter buffer is actively engaged. The jitter buffer is a component of the VeloCloud Edge's Dynamic Error Correction (DEC) capabilities, designed to mitigate network jitter and improve Quality of Experience (QoE) for real-time applications like voice and video. This command provides insights into the state and performance of the jitter buffer for individual traffic flows.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
```
example_com:velocli> debug --jitter
FDSN   FDSN_READ  LAST_LATE_FDSN  DEP_INTERVAL  JBUF_ENQUEUE  JBUF_DEQUEUE  JBUF_TDEQUEUE  SRC IP  DEST IP  SRC PORT  DEST PORT  PROTO  DSCP  APPLICATION  APP CLASS

example_com:velocli>
```

##  Field descriptions
| Column | Description |
|---|---|
| FDSN | Flow Data Sequence Number: A sequence number associated with the flow, likely representing the expected next packet. |
| FDSN_READ | Flow Data Sequence Number Read: The sequence number of the last packet read or processed for the flow. |
| LAST_LATE_FDSN | Last Late Flow Data Sequence Number: The sequence number of the most recent packet that arrived late for this flow. |
| DEP_INTERVAL | Departure Interval: The calculated interval (in milliseconds) at which packets are released from the jitter buffer to ensure smooth playout. |
| JBUF_ENQUEUE | Jitter Buffer Enqueue: The total number of packets enqueued into the jitter buffer for this flow. |
| JBUF_DEQUEUE | Jitter Buffer Dequeue: The total number of packets dequeued (played out normally) from the jitter buffer for this flow. |
| JBUF_TDEQUEUE | Jitter Buffer Timed Dequeue: The total number of packets that were dropped or timed out from the jitter buffer for this flow, often due to excessive delay. |
| SRC IP | Source IP Address: The source IP address of the traffic flow. |
| DEST IP | Destination IP Address: The destination IP address of the traffic flow. |
| SRC PORT | Source Port: The source port number of the traffic flow. |
| DEST PORT | Destination Port: The destination port number of the traffic flow. |
| PROTO | Protocol: The transport layer protocol of the flow (e.g., UDP, TCP). |
| DSCP | Differentiated Services Code Point: The DSCP marking of the packets in this flow, indicating its Quality of Service (QoS) priority. |
| APPLICATION | Application: An identifier for the application associated with this flow, as recognized by the Edge. |
| APP CLASS | Application Class: The class of the application (e.g., Real-time, Transactional, Bulk) which influences QoS and jitter buffer handling. |