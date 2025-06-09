#	--bgp_view [[all | dip] [all | segid] [all | ip_fam (v4 | v6)]]

##	Description
Displays the Border Gateway Protocol (BGP) routing table view from the perspective of the VeloCloud Edge. This command is segment-aware and provides details about BGP learned routes, including their attributes and status. It allows filtering by destination IP (dip), segment ID (segid), and IP address family (ip_fam: v4 or v6).

##  Arguments (optional)
If no arguments are provided, the command defaults to showing all BGP routes for all segments and IP families.

| Argument   | Description                                                                      |
|------------|----------------------------------------------------------------------------------|
| `all`      | Default for any position; shows all entries for that filter category.            |
| `dip`      | A specific destination IP prefix to filter the BGP routes (e.g., 192.168.1.0/24). |
| `segid`    | A specific segment ID to filter BGP routes for that segment.                     |
| `ip_fam`   | IP address family.                                                               |
| &nbsp;&nbsp; `v4` | Show only IPv4 BGP routes.                                                   |
| &nbsp;&nbsp; `v6` | Show only IPv6 BGP routes.                                                   |

The arguments are positional. For example, to filter by a specific segment ID (e.g., 1) and show only IPv4 routes, you would use `all 1 v4`. To filter by a destination IP for all segments and IP families, you might use `172.30.0.0/16 all all`.

##  Example usage
```
example_com:velocli> debug --bgp_view
Address            Netmask        Gateway         Nbr IP   Nbr ID  Metric  Type  Intf  Sync'd  Advertise  Inbound  Preference  LocalP  AspL  Reachable             Ptr   Age  SEG  Communities
172.30.0.0     255.255.0.0  172.30.255.36  172.30.255.36  0.0.0.0       0     E   any    RCVD       true    learn        1003     100     2        yes  0x7f5b76cc1680  6826    1
172.31.0.0   255.255.255.0  172.30.255.36  172.30.255.36  0.0.0.0       0     E   any    RCVD       true    learn        1003     100     2        yes  0x7f5b76cc1300  6826    1
```

##  Field descriptions
| Column      | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| Address     | The network address of the BGP route.                                                                      |
| Netmask     | The subnet mask for the network address.                                                                   |
| Gateway     | The next-hop gateway IP address for this BGP route.                                                        |
| Nbr IP      | The IP address of the BGP neighbor from which this route was learned.                                      |
| Nbr ID      | The BGP Router ID of the neighbor.                                                                         |
| Metric      | The BGP MED (Multi-Exit Discriminator) value for the route. Lower values are generally preferred.          |
| Type        | The type of BGP route (e.g., 'E' for EBGP - External BGP, 'I' for IBGP - Internal BGP).                    |
| Intf        | The interface associated with the route on the Edge (e.g., 'any').                                         |
| Sync'd      | Status of the route synchronization or processing state (e.g., 'RCVD' for Received).                       |
| Advertise   | Indicates if the Edge is advertising this route to its BGP peers (e.g., 'true', 'false').                  |
| Inbound     | Indicates how the route was acquired or its origin relative to the Edge (e.g., 'learn' for learned routes). |
| Preference  | The VeloCloud preference value for this BGP route. Used in route selection.                                |
| LocalP      | The BGP Local Preference attribute value. Higher values are preferred.                                     |
| AspL        | The length of the BGP AS_PATH attribute (number of ASNs in the path). Shorter paths are generally preferred. |
| Reachable   | Indicates if the destination network is considered reachable ('yes' or 'no').                              |
| Ptr         | An internal memory pointer to the route entry (primarily for debugging).                                   |
| Age         | The duration, in seconds, for which the route has been present in the BGP table.                           |
| SEG         | The VeloCloud segment ID to which this BGP route belongs.                                                  |
| Communities | BGP community values associated with the route, if any.                                                    |