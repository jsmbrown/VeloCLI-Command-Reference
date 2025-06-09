#	--nyansa_ep_nat_dump

##	Description
Dumps the Nyansa endpoint array, showing the destination IP and port, along with the source IP and interface used by the VeloCloud Edge for NATing traffic to these endpoints. This command is useful for understanding Network Address Translation (NAT) behavior for traffic, potentially from "special source IPs," directed towards Nyansa (now VMware Edge Network Intelligence) services, which provide network analytics.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --nyansa_ep_nat_dump
EndPontIP   DstPort  SourceIP  SourceInterface

example_com:velocli> 
```

##  Field descriptions
| Column          | Description |
|-----------------|-------------|
| EndPontIP       | The IP address of the Nyansa (VMware Edge Network Intelligence) endpoint/collector. |
| DstPort         | The destination port on the Nyansa endpoint to which the Edge sends traffic. |
| SourceIP        | The source IP address used by the VeloCloud Edge after NAT when sending traffic to the Nyansa endpoint. |
| SourceInterface | The VeloCloud Edge interface used to send the NATed traffic towards the Nyansa endpoint. |