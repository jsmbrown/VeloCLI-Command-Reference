#	--lacp_stats [all|<iface_name>]

##	Description
This command displays Link Aggregation Control Protocol (LACP) statistics for configured Link Aggregation Groups (LAGs) on the VeloCloud Edge. It provides details on LACP Protocol Data Units (PDUs) transmitted and received on both the aggregate LAG interface and its member (slave) interfaces.

##  Arguments (optional)
| Argument | Description |
|---|---|
| all | Displays LACP statistics for all configured LAG interfaces. This is the default behavior if no argument is specified. |
| <iface_name> | Displays LACP statistics for the specified LAG interface (e.g., LAG0, LAG1). |

##  Example usage
```
example_com:velocli> debug --lacp_stats
LAG Interface   Slave Interface  LACP PDU Tx Packets  LACP PDU Tx Bytes  LACP PDU Rx Packets  LACP PDU Rx Bytes

example_com:velocli> debug --lacp_stats LAG0
LAG Interface   Slave Interface  LACP PDU Tx Packets  LACP PDU Tx Bytes  LACP PDU Rx Packets  LACP PDU Rx Bytes
LAG0            GE1                     12345                789012             67890                432109
LAG0            GE2                     12340                788800             67885                432000
```
##  Field descriptions
| Column | Description |
|---|---|
| LAG Interface | The name of the Link Aggregation Group interface (e.g., LAG0). |
| Slave Interface | The name of the physical member interface that is part of the LAG (e.g., GE1, GE2). If no specific slave interface is shown for a row, the statistics might be aggregate for the LAG itself or indicate no active members. |
| LACP PDU Tx Packets | The number of LACP Protocol Data Unit packets transmitted by this interface. |
| LACP PDU Tx Bytes | The total number of bytes of LACP PDU packets transmitted by this interface. |
| LACP PDU Rx Packets | The number of LACP Protocol Data Unit packets received by this interface. |
| LACP PDU Rx Bytes | The total number of bytes of LACP PDU packets received by this interface. |