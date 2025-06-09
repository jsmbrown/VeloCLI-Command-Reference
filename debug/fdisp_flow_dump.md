#	--fdisp_flow_dump [core_id=<int>] [type=<str>] [protocol=<int>] [ip_tos=<int>] [src_port=<int>] [dst_port=<int>] [src_ip=<str>] [dst_ip=<str>] [ifindex=<int>] [discr=<int>] [discr_type=<int>]

##	Description
Displays detailed information about active flows managed by the flow-dispatcher in the VeloCloud Edge's dataplane. The flow-dispatcher is responsible for classifying incoming packets into flows and determining the appropriate processing actions. This command can be used to inspect the state of these flows, including their classification criteria, statistics, and the actions applied to them.

##  Arguments (optional)
The command can be run without arguments to display all flows. The following optional arguments can be used to filter the output:

| Argument         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `core_id=<int>`  | Filter flows processed by a specific CPU core ID.                           |
| `type=<str>`     | Filter flows by type (e.g., "user_flow").                                   |
| `protocol=<int>` | Filter flows by IP protocol number (e.g., 6 for TCP, 17 for UDP).           |
| `ip_tos=<int>`   | Filter flows by the IP Type of Service (TOS) or DSCP value.                 |
| `src_port=<int>` | Filter flows by source port number.                                         |
| `dst_port=<int>` | Filter flows by destination port number.                                    |
| `src_ip=<str>`   | Filter flows by source IP address.                                          |
| `dst_ip=<str>`   | Filter flows by destination IP address.                                     |
| `ifindex=<int>`  | Filter flows by the interface index (IfIndex) on which they were received.  |
| `discr=<int>`    | Filter flows by a specific discriminator value used for classification.     |
| `discr_type=<int>`| Filter flows by the type of discriminator.                                  |

##  Example usage
```
example_com:velocli> debug --fdisp_flow_dump
Core Id            Type  IfIndex  Proto         Discr          Src IP  Src Port          Dst IP  Dst Port  TOS  Paused  Refs  Size  Priv Size   Hits  Drops  Exceptions                                                                                                                              Actions
0             user_flow       21      6           1/1         1.2.3.4     60932   170.85.14.130      7000    0       N   2/0   256        112     12      0           5                                                check_for_exceptions, rx_account, prep_pkt_for_fwd, nat_ipv4_tcp_dst, send_pkt_v4_nvs
0             user_flow       11      6           1/0    172.30.1.200       179   172.30.255.36     63910    0       N   2/0   256        112    466      0         182                                                           check_for_exceptions, rx_account, prep_pkt_for_fwd, send_pkt_v4_routed_eth
0             user_flow       21      6           1/0      172.30.0.6        22   216.221.27.88      5155    0       N   2/0   256        112     53      0          24                                                           check_for_exceptions, rx_account, prep_pkt_for_fwd, send_pkt_v4_direct_eth
0             user_flow        2      6           1/1   172.30.255.37     54550    172.30.1.200       179    0       N   2/0   256        112      3      0           0                                                               check_for_exceptions, rx_account, prep_pkt_for_fwd, send_pkt_v4_routed
0             user_flow        1     17           1/0         8.8.8.8        53      172.30.0.6     10001    0       N   2/0   256        112      1      0           0                       check_for_exceptions, rx_account, nat_ipv4_udp_dst, prep_pkt_for_fwd, check_and_update_ttl, send_pkt_v4_routed
```

##  Field descriptions
| Column      | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| Core Id     | The identifier of the CPU core that is processing or owns this flow.                                       |
| Type        | The type of flow (e.g., `user_flow` for user traffic).                                                     |
| IfIndex     | The interface index of the network interface on which the first packet of this flow was received.          |
| Proto       | The IP protocol number of the flow (e.g., 6 for TCP, 17 for UDP, 1 for ICMP).                              |
| Discr       | Discriminator value(s) used for flow classification or identification, often shown as `value/type`.        |
| Src IP      | The source IP address of packets in this flow.                                                             |
| Src Port    | The source port number for TCP or UDP flows.                                                               |
| Dst IP      | The destination IP address of packets in this flow.                                                        |
| Dst Port    | The destination port number for TCP or UDP flows.                                                          |
| TOS         | The Type of Service (or DSCP) value from the IP header of packets in this flow.                            |
| Paused      | Indicates whether processing for this flow is currently paused ('Y' for yes, 'N' for no).                  |
| Refs        | Reference count for this flow entry, possibly indicating active users or internal references (e.g., `active/total`). |
| Size        | The memory size (in bytes) occupied by this flow entry.                                                    |
| Priv Size   | The size (in bytes) of private data associated with this flow entry.                                       |
| Hits        | The number of packets that have matched this flow entry.                                                   |
| Drops       | The number of packets belonging to this flow that have been dropped.                                       |
| Exceptions  | The number of packets in this flow that have triggered an exception or required special handling.          |
| Actions     | A list of actions performed on packets matching this flow (e.g., NAT, accounting, forwarding decision).    |