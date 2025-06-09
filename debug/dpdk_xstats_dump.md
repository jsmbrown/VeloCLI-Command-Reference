#	--dpdk_xstats_dump [intf [reset]]

##	Description
Displays extended statistics for Data Plane Development Kit (DPDK) managed network interfaces. These statistics provide detailed insights into packet processing performance and potential issues at the physical interface level.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `intf` | Specifies the network interface for which to display statistics (e.g., `eth0`, `GE1`). If omitted, statistics for all DPDK-managed interfaces are shown. |
| `reset` | If specified along with an `intf`, the extended statistics for that particular interface will be reset to zero after being displayed. This argument is only valid when an `intf` is also specified. |

##  Example usage
```
example_com:velocli> debug --dpdk_xstats_dump
{
  "eth0": {
    "rx_errors": 0,
    "rx_good_bytes": 41165263,
    "rx_good_packets": 49014,
    "rx_mbuf_allocation_errors": 0,
    "tx_errors": 0,
    "tx_good_bytes": 30876543,
    "tx_good_packets": 45001
  },
  "GE1": {
    "rx_errors": 5,
    "rx_good_bytes": 102458976,
    "rx_good_packets": 98765,
    "rx_mbuf_allocation_errors": 1,
    "tx_errors": 2,
    "tx_good_bytes": 98765432,
    "tx_good_packets": 87654
  }
}
```
##  Field descriptions
The output is a JSON object where each key is an interface name (e.g., "eth0", "GE1"). Each interface object contains the following key-value pairs:

| Field                       | Description |
|-----------------------------|-------------|
| `rx_errors`                 | The total number of erroneous packets received on the interface. This can include packets with CRC errors, framing errors, or other physical layer issues. |
| `rx_good_bytes`             | The total number of bytes successfully received on the interface, excluding any bytes from erroneous packets. |
| `rx_good_packets`           | The total number of packets successfully received on the interface without errors. |
| `rx_mbuf_allocation_errors` | The number of times the system failed to allocate memory buffers (mbufs) for incoming packets on this interface. This can indicate memory pressure or configuration issues. |
| `tx_errors`                 | The total number of errors encountered during packet transmission on the interface. |
| `tx_good_bytes`             | The total number of bytes successfully transmitted on the interface. |
| `tx_good_packets`           | The total number of packets successfully transmitted on the interface. |