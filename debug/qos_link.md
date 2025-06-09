#	--qos_link &lt;peer_id | local&gt; &lt;stats | clear_drops&gt;

##	Description
Provides a debug interface for Quality of Service (QoS) mechanisms operating on VeloCloud SD-WAN overlay paths (tunnels) to peers, or on local WAN interfaces. This command allows users to inspect detailed QoS statistics such as packet/byte counts and drop counts per queue and traffic class, or to clear these drop counters. This is useful for troubleshooting QoS policy enforcement, identifying congestion points, and verifying the behavior of traffic prioritization. The `clear_drops` action will typically output a confirmation message upon success.

##  Arguments
The command requires two positional arguments: a target specifier and an action specifier.

| Argument | Description |
|---|---|
| `<peer_id | local>` | **Target Specifier (First positional argument)** <br> Determines the scope of the QoS information. <br> - `<peer_id>`: The logical ID (e.g., `01234567-89ab-cdef-0123-456789abcdef`) of a remote VeloCloud Edge or Gateway. The command will focus on QoS for the SD-WAN overlay paths (tunnels) established with this peer. <br> - `local`: The command will focus on QoS aspects related to the local VeloCloud Edge itself, such as statistics for its physical WAN interfaces or overall local QoS processing. |
| `<stats | clear_drops>` | **Action Specifier (Second positional argument)** <br> Determines the operation to perform on the specified target. <br> - `stats`: Display current QoS statistics. This typically includes packet counts, byte counts, and drop counts for various QoS queues and traffic classes. <br> - `clear_drops`: Clear existing QoS-related packet drop counters for the specified target. |

##  Example Usage
### Displaying QoS statistics for paths to a specific peer:
```
example_com:velocli> debug --qos_link 01234567-89ab-cdef-0123-456789abcdef stats

Link to Peer 01234567-89ab-cdef-0123-456789abcdef (Remote-Branch-Edge-01):
  Path ID: tunnel0.9876 (Interface: GE1, WAN Link: MPLS_Primary, Public IP: 198.51.100.10)
    Queue   Class         Packets TX   Bytes TX     Drops TX   Packets RX   Bytes RX     Drops RX
    -----   -----------   -----------  -----------  ---------  -----------  -----------  ---------
    0       Realtime      150230       18056700     15         140120       17056700     2
    1       Transactional 750050       905000700    252        700030       855000700    30
    2       Bulk          2500080      3200567080   850        2400060      3100567080   110

  Path ID: tunnel0.9877 (Interface: GE2, WAN Link: INET_Backup, Public IP: 203.0.113.20)
    Queue   Class         Packets TX   Bytes TX     Drops TX   Packets RX   Bytes RX     Drops RX
    -----   -----------   -----------  -----------  ---------  -----------  -----------  ---------
    0       Realtime      98765        10987600     8          88760        9987600      1
    1       Transactional 432100       551234500    130        402150       521234500    15
    2       Bulk          1987650      2109876500   510        1887600      2009876500   65
```
### Clearing QoS drop counters for local WAN interfaces:
```
example_com:velocli> debug --qos_link local clear_drops
Local QoS drop counters cleared.
```

##  Field Descriptions
The following descriptions apply to the output of the `stats` action when a `<peer_id>` is specified:

| Column | Description |
|---|---|
| `Link to Peer ... (Peer Name)` | Identifies the remote peer (Edge or Gateway) for which QoS path statistics are displayed. Includes the peer's logical ID and its configured name. |
| `Path ID` | The identifier for a specific SD-WAN overlay path (tunnel) to the peer. Additional context provided includes: <br> - `Interface`: The physical interface on the local Edge used for this path (e.g., GE1, GE2). <br> - `WAN Link`: The user-configured name of the WAN link associated with this path. <br> - `Public IP`: The public IP address used by the local Edge for this path. |
| `Queue` | The internal QoS queue number. VeloCloud Edges use multiple queues to enforce traffic prioritization based on Business Policies. |
| `Class` | The traffic class associated with the queue (e.g., `Realtime`, `Transactional`, `Bulk`). These classes are defined in the Business Policy configuration and map different types of application traffic to specific queues and priority levels. |
| `Packets TX` | The total number of packets transmitted (TX) on this queue for this specific path since the counters were last reset. |
| `Bytes TX` | The total number of bytes transmitted (TX) on this queue for this specific path since the counters were last reset. |
| `Drops TX` | The total number of packets dropped from the transmit (TX) queue for this path. Drops typically occur due to network congestion when the queue is full, or as a result of QoS shaping/policing actions. |
| `Packets RX` | The total number of packets received (RX) on this queue for this specific path since the counters were last reset. |
| `Bytes RX` | The total number of bytes received (RX) on this queue for this specific path since the counters were last reset. |
| `Drops RX` | The total number of packets dropped from the receive (RX) path processing associated with this queue. Receive drops are less common for QoS reasons but can occur due to ingress policing or other factors. |

**Note:** The output format for `debug --qos_link local stats` may differ, typically showing QoS statistics aggregated per local WAN interface and direction (TX/RX) rather than per peer path.