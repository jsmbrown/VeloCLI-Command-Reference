#	--ifaces [name=<str>|descr=<str>|driver=<str>|netdev=<str>|mgmt_type=<str>|encap_type=<str>|oper_state=<str>|ifindex=<int>]

##	Description
Displays a list of network interfaces on the VeloCloud Edge, along with their status, statistics, and configuration details. This command can be used to troubleshoot interface-related issues, verify IP addressing, and monitor traffic.

##  Arguments (optional)
The command can be run without arguments to display all interfaces. Alternatively, one or more of the following filter arguments can be used to narrow down the results:

| Argument | Description |
|---|---|
| `name=<str>` | Filters interfaces by their logical name (e.g., GE1, GE2, SFP1). |
| `descr=<str>` | Filters interfaces by their user-defined description. |
| `driver=<str>` | Filters interfaces by their driver type (e.g., dpdk, tun, null). |
| `netdev=<str>` | Filters interfaces by their network device name (e.g., eth0, eth1). |
| `mgmt_type=<str>` | Filters interfaces by their management type (e.g., static, dhcp). |
| `encap_type=<str>` | Filters interfaces by their encapsulation type (e.g., none, vlan). |
| `oper_state=<str>` | Filters interfaces by their operational state (e.g., UP/RUNNING, DOWN). |
| `ifindex=<int>` | Filters interfaces by their unique interface index number. |

##  Example usage
```
example_com:velocli> debug --ifaces
IfIndex                                              Name (Descr)    Driver         State          IP Addr  IPv6 Addr List  Caps  Rx Packets/Pps  Rx Bytes/Average  Rx Dropped  Rx Errors  Tx Packets/Pps  Tx Bytes/Average  Tx Dropped  Tx Errors
1                                                        GE1/eth0      dpdk    UP/RUNNING    172.30.0.6/24                               43724/6      40379334/171           0          0        42472/10      10463569/248           0          0
2                                                        GE2/eth1      dpdk    UP/RUNNING  172.30.1.200/24                                3978/0         260260/66           0          0           664/0          49808/86           0          0
3                                                     qsec1/qsec1       tun    UP/RUNNING                                                   11/0            528/48           0          0           326/0         36988/112           0          0
4                                                     null0/null0      null    UP/RUNNING        0.0.0.0/0                                   0/0               0/0           0          0             0/0               0/0           0          0
5                                                     null1/null1      null    UP/RUNNING        0.0.0.0/0                                   0/0               0/0           0          0             0/0               0/0           0          0
```

##  Field descriptions
| Column | Description |
|---|---|
| `IfIndex` | The unique numerical identifier for the interface. |
| `Name (Descr)` | The logical name of the interface (e.g., GE1) and its underlying network device name (e.g., eth0). A user-defined description may also appear here if configured. |
| `Driver` | The driver type used by the interface (e.g., `dpdk` for Data Plane Development Kit accelerated interfaces, `tun` for tunnel interfaces, `null` for null interfaces). |
| `State` | The operational state of the interface (e.g., `UP/RUNNING`, `DOWN`). |
| `IP Addr` | The IPv4 address and subnet mask configured on the interface (e.g., `172.30.0.6/24`). |
| `IPv6 Addr List` | A list of IPv6 addresses configured on the interface. This field may be empty if no IPv6 addresses are configured. |
| `Caps` | Interface capabilities (not explicitly detailed in the example output but represents flags for features like promiscuous mode, multicast, etc.). |
| `Rx Packets/Pps` | Total number of packets received on the interface, followed by the current receive rate in packets per second (Pps). |
| `Rx Bytes/Average` | Total number of bytes received on the interface, followed by the average size of received packets in bytes. |
| `Rx Dropped` | Total number of received packets dropped by the interface, often due to buffer overflows or other receive-side issues. |
| `Rx Errors` | Total number of errors encountered during packet reception (e.g., CRC errors, frame errors). |
| `Tx Packets/Pps` | Total number of packets transmitted from the interface, followed by the current transmit rate in packets per second (Pps). |
| `Tx Bytes/Average` | Total number of bytes transmitted from the interface, followed by the average size of transmitted packets in bytes. |
| `Tx Dropped` | Total number of transmitted packets dropped by the interface, often due to queue overflows or other transmit-side issues. |
| `Tx Errors` | Total number of errors encountered during packet transmission. |