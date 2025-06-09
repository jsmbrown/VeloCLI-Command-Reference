#	--advertise_ospf_prefix [[all | <prefix>] [0 | 1]]

##	Description
Debug option to control the advertisement of OSPF (Open Shortest Path First) prefixes learned by the VeloCloud Edge to VeloCloud Gateways (VCG) for redistribution to the overlay. This command allows an administrator to selectively enable or disable the propagation of specific OSPF routes into the SD-WAN overlay network. This can be useful for troubleshooting routing issues or managing route advertisements in complex OSPF environments connected to the SD-WAN.

##  Arguments (optional)
If no arguments are provided, the command displays help information. To control prefix advertisement, both a selector (`all` or `<prefix>`) and an action (`0` or `1`) must be specified.

| Argument   | Description                                                                                                                               |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all` \| `IPv4 prefix` | Specifies the OSPF prefix(es) to be managed. <br> - `all`: Applies the action to all OSPF prefixes eligible for advertisement to the VCG. <br> - `IPv4 prefix`: The specific IPv4 prefix in CIDR notation (e.g., `192.168.100.0/24`) to be advertised or withdrawn. |
| `0` \| `1` | Determines the action to be taken for the specified prefix(es). <br> - `0`: Stop advertising (withdraw) the prefix(es) from the VCG. <br> - `1`: Start advertising the prefix(es) to the VCG. |          |

##  Example usage
To enable advertising the specific OSPF prefix `10.100.5.0/24` to VeloCloud Gateways:
```
example_com:velocli> debug --advertise_ospf_prefix 10.100.5.0/24 1
{
  "advertise_ospf_prefix": "success"
}
```

To disable advertising all learned OSPF prefixes to VeloCloud Gateways:
```
example_com:velocli> debug --advertise_ospf_prefix all 0
{
  "advertise_ospf_prefix": "success"
}
```

##  Field descriptions
This command is used to modify the OSPF prefix advertisement behavior and does not produce a tabular data output. Successful execution results in a simple confirmation message. The effect of the command (i.e., whether prefixes are being advertised or not) would need to be verified using other `show` commands related to OSPF status, routing tables on the Edge, or by observing route propagation on the VeloCloud Gateways.