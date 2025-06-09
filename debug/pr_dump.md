#	--pr_dump [logical-id | all]

##	Description
Dumps detailed peer reachability information maintained by the VeloCloud Edge. This command provides insights into the status and quality of VeloCloud Management Protocol (VCMP) tunnels established with other VeloCloud Edges and Gateways. This information is critical for diagnosing overlay connectivity issues, understanding path selection, and verifying the health of the SD-WAN fabric.

##	Arguments (optional)
| Argument    | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| `logical-id`| Specifies the unique logical identifier of a remote VeloCloud Edge or Gateway. If provided, the command will dump reachability information specifically for this peer. |
| `all`       | Dumps reachability information for all known VeloCloud peer Edges and Gateways. This is typically the default behavior if no argument is specified. |
| *none*      | If no argument is provided, it usually defaults to `all`.                                                  |

##	Example Usage
```
example_com:velocli> debug --pr_dump
```
**(Note: The output below is a conceptual representation. The actual format and details may vary.)**
```
Peer Reachability Dump:

Peer: BranchOffice-123 (Logical ID: 01234567-89ab-cdef-0123-456789abcdef)
  State: REACHABLE
  Last Heard: 2023-11-15 10:20:30 UTC (0 seconds ago)
  Best Path ID: 101 (WAN1_GE1)
  VCMP Tunnels:
    Tunnel ID: 1 (Path ID: 101)
      Interface: GE1 (Public IP: 198.51.100.10, Private IP: 10.1.1.10)
      Link Name: WAN1_GE1
      Type: Public Wired
      Remote IP: 203.0.113.50 (Gateway-Primary)
      Status: UP
      Rx Packets: 15000, Tx Packets: 12500
      Rx Bytes: 12MB, Tx Bytes: 10MB
      Latency: 15ms, Jitter: 2ms, Loss: 0.01%
      Bandwidth (Up/Down): 95 Mbps / 98 Mbps
      DEC: Enabled

    Tunnel ID: 2 (Path ID: 102)
      Interface: GE2 (Public IP: 198.51.100.11, Private IP: 10.1.2.10)
      Link Name: WAN2_LTE
      Type: Public Wireless
      Remote IP: 203.0.113.50 (Gateway-Primary)
      Status: UP (Standby)
      Rx Packets: 500, Tx Packets: 400
      Rx Bytes: 0.5MB, Tx Bytes: 0.4MB
      Latency: 60ms, Jitter: 15ms, Loss: 0.5%
      Bandwidth (Up/Down): 15 Mbps / 10 Mbps
      DEC: Enabled

Peer: Hub-Datacenter (Logical ID: fedcba98-7654-3210-fedc-ba9876543210)
  State: UNREACHABLE
  Last Heard: 2023-11-15 09:15:00 UTC (1 hour 5 minutes ago)
  Best Path ID: N/A
  VCMP Tunnels:
    Tunnel ID: 3 (Path ID: 201)
      Interface: GE1 (Public IP: 198.51.100.10, Private IP: 10.1.1.10)
      Link Name: WAN1_GE1
      Type: Public Wired
      Remote IP: 192.0.2.100 (Hub-Datacenter)
      Status: DOWN
      Last Error: Keepalive Timeout
      ... (other metrics if available) ...

... (additional peers) ...
```

##	Key Information Provided
The output of `--pr_dump` is a detailed diagnostic dump. While not strictly columnar, it generally includes the following information for each peer:

| Information Category | Description                                                                                                |
|----------------------|------------------------------------------------------------------------------------------------------------|
| **Peer Identification** |                                                                                                            |
| Peer Name/Logical ID | The hostname or unique logical identifier of the remote VeloCloud Edge or Gateway.                           |
| **Overall Status**   |                                                                                                            |
| State                | The overall reachability status of the peer (e.g., REACHABLE, UNREACHABLE, DEGRADED).                      |
| Last Heard           | Timestamp of the last successful communication received from the peer, and how long ago.                   |
| Best Path ID         | Identifier of the currently preferred path to this peer, if applicable.                                    |
| **VCMP Tunnel Details** | For each tunnel (path) to the peer:                                                                        |
| Tunnel ID            | A unique identifier for the VCMP tunnel.                                                                   |
| Path ID              | Identifier for the underlying network path used by the tunnel.                                             |
| Interface            | The local physical or logical interface (e.g., GE1, SFP1, PPPoE) used for this tunnel.                     |
| Link Name            | The configured name for the WAN link.                                                                      |
| IP Addresses         | Local public and private IP addresses associated with the path.                                            |
| Remote IP            | The IP address of the remote peer on this specific path.                                                   |
| Type                 | The type of link (e.g., Public Wired, Public Wireless, Private MPLS).                                      |
| Status               | The operational status of the individual tunnel (e.g., UP, DOWN, NEGOTIATING, STANDBY).                    |
| Traffic Statistics   | Received (Rx) and Transmitted (Tx) packets and bytes over the tunnel.                                      |
| Quality Metrics      | Performance metrics for the tunnel, such as Latency, Jitter, and Packet Loss. This may reflect measurements before or after Dynamic Error Correction (DEC). |
| Bandwidth            | Measured or estimated uplink and downlink bandwidth for the path.                                          |
| DEC Status           | Indicates if Dynamic Error Correction is active or enabled for this path.                                  |
| Last Error           | If a tunnel is down or experiencing issues, this may show the last recorded error message.                 |