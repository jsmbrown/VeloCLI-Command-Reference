#	--ospf_info [v4 | v6 | all]

##	Description
Displays the OSPF (Open Shortest Path First) settings and the status of OSPF neighbors for both IPv4 and IPv6 address families. This command is useful for troubleshooting OSPF adjacencies and verifying OSPF configuration on the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4 | Displays OSPF information for IPv4 only. |
| v6 | Displays OSPF information for IPv6 only. |
| all | Displays OSPF information for both IPv4 and IPv6 (this is the default if no argument is provided). |

##  Example usage
```
example_com:velocli> debug --ospf_info
{
  "ospf6_info": [],
  "ospf_info": []
}

example_com:velocli>
```
##  Field descriptions
| Field | Description |
|---|---|
| ospf6_info | An array containing OSPFv3 (for IPv6) information. This will include details about OSPFv3 areas, interfaces, and neighbor states if OSPFv3 is configured and active. If empty, it indicates no OSPFv3 information is available or configured. |
| ospf_info | An array containing OSPFv2 (for IPv4) information. This will include details about OSPFv2 areas, interfaces, and neighbor states if OSPFv2 is configured and active. If empty, it indicates no OSPFv2 information is available or configured. |