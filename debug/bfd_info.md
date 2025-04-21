#	--bfd_info [[all | segment-id] [[v4 | v6 | all]]]

##	Description
Summary of BFD configuration and neighbor states

##  Arguments (optional)
| Argument | Description |
|---|---|
| none (or 'all') | Display all BFD peers |
| segment-id | Numerical ID of the segment to display BFD peers from |
| v4 | Display only IPv4 peers |
| v6 | Display only IPv6 peers |
| all | Display both IPv4 and IPv6 peers |

##  Example usage
```
example_com:velocli> debug --bfd_info 0 v4
Peer Address      Local Address  Segment Id  Detect Multiplier  Transmit Interval  Receive Interval  Multihop  State     Up/Down Time
192.168.10.202   192.168.10.201           0                  3                300               300     False     UP  9 days, 3:04:15
```

##  Field descriptions
| Column | Description |
|---|---|
| Peer Address | BFD Peer IP address |
| Local Address | Local BFD source address |
| Segment Id | Numerical ID of the segment in which the peer is configured |
| Detect Multiplier | Configured detect multiplier for the session specifying the number of consecutive BFD echo packets that can be missed before declaring the connection down |
| Transmit Interval | Configured transmit interval for the session specifying how often BFD echo packets are sent |
| Receive Interval | Negotiated interval specifying how often BFD echo packets should be received from the peer |
| Multihop | True/False value indicating whether the path to the peer traverses L3 hop(s) |
| State | UP/DOWN state of the session with the peer |
| Up/Down Time | Amount of time that the session has been in the current state |