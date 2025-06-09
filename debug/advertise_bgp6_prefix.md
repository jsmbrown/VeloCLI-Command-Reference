#	--advertise_bgp6_prefix [all | IPv6 prefix] [0 | 1] [all | segment-id]

##	Description
This debug command is used to manually advertise or withdraw an IPv6 BGP prefix to VeloCloud Gateways (VCG) for redistribution to the overlay. It is typically used for troubleshooting BGPv6 advertisements or testing routing policies related to IPv6 prefixes within a specific segment or across all segments.

##  Arguments (optional)
The command requires three positional arguments that define the prefix, the action (advertise/withdraw), and the scope (segment).

| Argument      | Description                                                                                                                               |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all` \| `IPv6 prefix` | Specifies the BGPv6 prefix(es) to be managed. <br> - `all`: Applies the action to all BGP prefixes eligible for advertisement to the VCG. <br> - `IPv6 prefix`: The specific IPv4 prefix in CIDR notation (e.g., `2001:db8:acad::/48`) to be advertised or withdrawn. |
| `0` \| `1` | Determines the action to be taken for the specified prefix(es). <br> - `0`: Stop advertising (withdraw) the prefix(es) from the VCG. <br> - `1`: Start advertising the prefix(es) to the VCG. |
| `all` \| `segment-id` | Defines the scope of the command in terms of network segments. <br> - `all`: The action applies to all configured segments on the Edge. <br> - `segment-id`: The numerical identifier of a specific segment to which the BGP advertisement control should apply. |

##  Example usage
The command requires specific arguments to perform an action. For instance, to advertise an IPv6 prefix `2001:db8:acad::/48` for segment `1`:
```
example_com:velocli> debug --advertise_bgp6_prefix 2001:db8:acad::/48 1 1
{
  "advertise_bgp6_prefix": "success"
}
```

To withdraw the same IPv6 prefix `2001:db8:acad::/48` for segment `1`:
```
example_com:velocli> debug --advertise_bgp6_prefix 2001:db8:acad::/48 0 1
{
  "advertise_bgp6_prefix": "success"
}
```

##  Field descriptions
| Column | Description |
|---|---|
| N/A    | This command is used to trigger an action (advertising or withdrawing a BGP6 prefix) and does not produce tabular output. Only confirmation or error messages related to the execution of the command are printed to the console. |