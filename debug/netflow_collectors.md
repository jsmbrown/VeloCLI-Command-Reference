#	--netflow_collectors

##	Description
This command displays the configured NetFlow collectors on the VeloCloud Edge. NetFlow is a network protocol developed by Cisco for collecting IP traffic information and monitoring network flow. VeloCloud Edges can be configured to export flow data to one or more NetFlow collectors for analysis and reporting.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --netflow_collectors
CollectorId   SegmentId             IP  Port  AllowAll  SourceIP  SourceInterface  InterfaceSelection
0                     1  10.100.101.10  4739     False   1.2.3.4              LO2           Automatic

example_com:velocli>
```

##  Field descriptions
| Column             | Description                                                                                                |
|--------------------|------------------------------------------------------------------------------------------------------------|
| CollectorId        | A unique identifier for the NetFlow collector configuration.                                               |
| SegmentId          | The ID of the network segment for which NetFlow data is being collected and exported.                      |
| IP                 | The IP address of the NetFlow collector server.                                                            |
| Port               | The UDP port number on which the NetFlow collector server is listening for incoming NetFlow data.          |
| AllowAll           | Indicates if NetFlow data from all segments is allowed. When false, only flows from the segment in which the collector is configured will be sent |
| SourceIP           | The source IP address used by the Edge when sending NetFlow data to the collector.                         |
| SourceInterface    | The specific interface on the Edge used to source the NetFlow traffic.                                     |
| InterfaceSelection | Specifies how the source interface was selected (e.g., automatic, specific interface name).                |