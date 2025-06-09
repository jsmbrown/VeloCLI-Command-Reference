#	--dpdk_ports_dump [interface physical name]

##	Description
This command displays detailed information about Data Plane Development Kit (DPDK) ports on the VeloCloud Edge. DPDK is a set of libraries and drivers for fast packet processing. This command is useful for troubleshooting physical and virtual interface issues related to packet processing performance.

##  Arguments (optional)
| Argument | Description |
|---|---|
| interface physical name | Specifies the physical name of an interface (e.g., `eth0`, `eth1`) to display information for that specific port. If omitted, information for all DPDK ports is displayed. |

##  Example usage
```
example_com:velocli> debug --dpdk_ports_dump
name     type  port  link  ignore  strip  speed  duplex  autoneg  driver  num_txq  txq_size  num_rxq  rxq_size
eth0   packet     0     1       0      1  50000       1        0  packet        1      4096        1      4096
eth1   packet     1     1       0      1  50000       1        0  packet        1      4096        1      4096
vce1    vhost     2     1       0      0  50000       1        0                1         0        1         0

example_com:velocli>
```
##  Field descriptions
| Column | Description |
|---|---|
| name | The logical name of the interface (e.g., eth0, eth1, vce1). |
| type | The type of the DPDK port. Common types include `packet` (for physical interfaces) and `vhost` (for virtual interfaces, often used with VNFs). |
| port | The internal DPDK port ID. |
| link | Indicates the link status of the port. `1` typically means the link is up, and `0` means the link is down. |
| ignore | A flag indicating if the port is being ignored by the system for packet processing. `0` means not ignored, `1` means ignored. |
| strip | Indicates if VLAN tag stripping is enabled on the port. `1` means enabled, `0` means disabled. |
| speed | The configured or negotiated speed of the port in Mbps (Megabits per second). |
| duplex | Indicates the duplex mode of the port. `1` typically means full-duplex, and `0` might indicate half-duplex or an unknown state. |
| autoneg | Indicates if autonegotiation is enabled for the port's speed and duplex settings. `1` means enabled, `0` means disabled or not applicable. |
| driver | The name of the DPDK driver managing this port. |
| num_txq | The number of transmit queues (TX queues) configured for this port. Multiple queues can help improve transmit performance. |
| txq_size | The size (number of descriptors) of each transmit queue. |
| num_rxq | The number of receive queues (RX queues) configured for this port. Multiple queues can help improve receive performance, especially on multi-core CPUs. |
| rxq_size | The size (number of descriptors) of each receive queue. |