#	--mcr_dump

##	Description
This command displays all multicast routes known by the VeloCloud Edge. Multicast routing enables the efficient distribution of one-to-many traffic, such as video conferencing or streaming services, across the SD-WAN fabric.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --mcr_dump
Segment   Source  Group  IIF  OIL

example_com:velocli>
```
*(Note: The example output provided is empty, indicating no active multicast routes at the time of command execution. A populated output would list the active multicast routes.)*

##  Field descriptions
| Column  | Description                                                                 |
| :------ | :-------------------------------------------------------------------------- |
| Segment | The segment ID to which the multicast route belongs.                        |
| Source  | The source IP address of the multicast stream.                              |
| Group   | The destination multicast group IP address.                                 |
| IIF     | Incoming Interface. The interface on which the multicast traffic is received. |
| OIL     | Outgoing Interface List. The list of interfaces to which the multicast traffic is forwarded. |