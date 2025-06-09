#	--suricata_config_dump

##	Description
This command fetches and displays the current configuration parameters from the Suricata Intrusion Detection/Prevention System (IDS/IPS) module running on the VeloCloud Edge. Suricata is a high-performance Network IDS, IPS, and Network Security Monitoring engine. This command is useful for inspecting the operational parameters of the Suricata instance, which can be part of a VNF (Virtual Network Function) deployment on the Edge.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --suricata_config_dump
Attribute                                 value
max-pending-packets                       16536
flow.memcap                           261414912
flow.hash-size                            65536
flow.prealloc                             35518
stream.memcap                         247704624
```

##  Field descriptions
| Column      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| Attribute   | The name of the Suricata configuration parameter.                           |
| value       | The current configured value for the corresponding Suricata attribute.        |