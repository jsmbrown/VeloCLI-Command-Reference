#	--seg_nat_dump

##	Description
This command displays the Network Address Translation (NAT) table specific to segments configured on the VeloCloud Edge. It provides insights into how traffic originating from different segments is being translated, including source and destination IP addresses, ports, protocols, and the interfaces involved. This is useful for troubleshooting NAT-related connectivity issues for segmented networks.

##  Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --seg_nat_dump
AppName       SegmentId           CollectorIP  DstPort  Proto      SourceIP  SourceInterface  InterfaceSelection  TxCount  RxCount
SSH                   0         216.221.27.88     5008    TCP    172.30.0.6              GE1           Automatic       82       89
SSH                   0         216.221.27.88     5080    TCP    172.30.0.6              GE1           Automatic       46       55
SSH                   0         216.221.27.88     5007    TCP    172.30.0.6              GE1           Automatic       91      101
SSH                   0         216.221.27.88     5056    TCP    172.30.0.6              GE1           Automatic       59       60
SSH                   0         216.221.27.88     5075    TCP    172.30.0.6              GE1           Automatic       42       54
```

##  Field descriptions
| Column | Description |
|---|---|
| AppName | The name of the application associated with the NAT entry. |
| SegmentId | The identifier of the network segment from which the traffic originates. |
| CollectorIP | The IP address of the destination (often a VeloCloud Gateway or a remote collector) after NAT. |
| DstPort | The destination port number of the translated traffic. |
| Proto | The transport layer protocol used (e.g., TCP, UDP). |
| SourceIP | The original source IP address of the traffic before NAT. |
| SourceInterface | The VeloCloud Edge interface through which the traffic is routed post-NAT. |
| InterfaceSelection | The method used for selecting the egress interface (e.g., Automatic, User Defined). |
| TxCount | The number of packets transmitted for this NAT entry. |
| RxCount | The number of packets received for this NAT entry. |