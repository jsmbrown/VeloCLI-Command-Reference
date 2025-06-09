#	--advertise_bgp_prefix [all | IPv4 prefix] [0 | 1] [all | segment-id]

##	Description
This debug command allows for manual control over Border Gateway Protocol (BGP) prefix advertisements from the VeloCloud Edge to a VeloCloud Gateway (VCG) for redistribution to the overlay. It can be used to instruct the Edge to either start (advertise) or stop (withdraw) advertising specific or all BGP prefixes for a particular network segment or all segments. This functionality is typically used for troubleshooting BGP routing behavior or for specific testing scenarios within the SD-WAN overlay.

##  Arguments
| Argument | Description |
|---|---|
| `all` \| `IPv4 prefix` | Specifies the BGP prefix(es) to be managed. <br> - `all`: Applies the action to all BGP prefixes eligible for advertisement to the VCG. <br> - `IPv4 prefix`: The specific IPv4 prefix in CIDR notation (e.g., `192.168.100.0/24`) to be advertised or withdrawn. |
| `0` \| `1` | Determines the action to be taken for the specified prefix(es). <br> - `0`: Stop advertising (withdraw) the prefix(es) from the VCG. <br> - `1`: Start advertising the prefix(es) to the VCG. |
| `all` \| `segment-id` | Defines the scope of the command in terms of network segments. <br> - `all`: The action applies to all configured segments on the Edge. <br> - `segment-id`: The numerical identifier of a specific segment to which the BGP advertisement control should apply. |

##  Example usage
```
# To start advertising the BGP prefix 172.16.50.0/24 to the VeloCloud Gateway for segment ID 1:
example_com:velocli> debug --advertise_bgp_prefix 172.16.50.0/24 1 1
{
  "advertise_bgp_prefix": "success"
}

# To stop advertising all BGP prefixes to the VeloCloud Gateway across all segments:
example_com:velocli> debug --advertise_bgp_prefix all 0 all
{
  "advertise_bgp_prefix": "success"
}
```

##  Field descriptions
This command is primarily a control and debugging tool. Its output consists of:
*   A confirmation message indicating whether the request to advertise or withdraw the BGP prefix(es) was successfully processed by the Edge.
*   Error messages if the arguments are invalid or if the operation cannot be performed.