#	--static_routes [v4 | v6 | all]

##	Description
Dumps the current static routes table configured on the VeloCloud Edge. Static routes are manually configured paths for IP traffic, often used to direct traffic to specific destinations that are not learned dynamically via routing protocols like BGP or OSPF, or through the VeloCloud overlay. This command allows viewing IPv4, IPv6, or all static routes.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4 | Displays only IPv4 static routes. |
| v6 | Displays only IPv6 static routes. |
| all | Displays all static routes (both IPv4 and IPv6). This is the default if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --static_routes v4
Address                Netmask    Next Hop                           Destination    Type  Interface  Metric  VLAN  SegId
172.30.255.0     255.255.255.0  172.30.1.1  00000000-0000-0000-0000-000000000000     WAN        GE2       0   N/A      1
169.254.4.4    255.255.255.255     0.0.0.0  954dd5f7-8aeb-428b-bb4b-f6ce35f5e539  GW-NSD        any       5   N/A      2
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The destination network IP address for the static route. |
| Netmask | The subnet mask for the destination network. |
| Next Hop | The IP address of the next hop router or device to which packets for the destination network should be forwarded. |
| Destination | The Logical ID of the destination. For underlay static routes (e.g., Type WAN), this may be a placeholder like `00000000-0000-0000-0000-000000000000`. For overlay static routes, this would be the Logical ID of the target VeloCloud Edge or Gateway. |
| Type | Indicates the type of interface or path for the static route (e.g., WAN for an underlay path, GW-NSD for NSD via gateway, etc.). |
| Interface | The specific network interface (e.g., GE2, SFP1) on the VeloCloud Edge through which traffic for this static route will be sent. (`any` for none interface specific static routes like NSDs) |
| Metric | The administrative cost associated with this static route. Lower metrics are generally preferred. |
| VLAN | The VLAN ID associated with the interface for this route, if applicable. "N/A" indicates no specific VLAN is configured for this route entry. |
| SegId | The Segment ID to which this static route applies. Segmentation allows for logical partitioning of network traffic. |