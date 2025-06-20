#	--dc_routes [all|prefix] [all|segment-id]

##	Description
Dumps the datacenter route table. This table contains routes learned from non-SD-WAN destinations (NSDs) within the VeloCloud SD-WAN overlay.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` or `prefix` | Filters the output. `all` displays all datacenter routes. `prefix` allows you to specify a particular IP prefix (e.g., 192.168.100.0/24) to display routes for. |
| `all` or `segment-id` | Filters the output by segment. `all` displays routes across all segments. `segment-id` allows you to specify a particular segment ID to display routes for that segment. |

##  Example usage
```
example_com:velocli> debug --dc_routes
Address                 Netmask        Type  Gateway                           Next Hop ID                         Dst LogicalId  Reachable  Metric  Preference  Flags  Vlan  Intf  MTU
169.254.4.4     255.255.255.255  datacenter      any  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  954dd5f7-8aeb-428b-bb4b-f6ce35f5e539       True       5           0     SR     0   any  N/A
0.0.0.0         255.255.255.255  datacenter      any  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  88616e5e-e59b-406e-9c1e-39cd29cc9385      False       0           0    SRc     0   any  N/A
0.0.0.0         255.255.255.255  datacenter      any  c8d0a769-1daf-4670-91ad-5b038ea9b4d6  f3598a75-8531-4636-ad69-eb48a816034c      False       0           0    SRc     0   any  N/A
192.168.176.0     255.255.254.0  datacenter      any  2bbfbb2b-4ee0-46a1-b394-01d8194f97b8  954dd5f7-8aeb-428b-bb4b-f6ce35f5e539       True       0         999    SBR     0   any  N/A
P - PG, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, n - nonVelocloud, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS, I - IPSec, G - GRE
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The destination IP address for the route. |
| Netmask | The subnet mask for the destination IP address. |
| Type | The type of route (will always be `datacenter` in this command's output). |
| Gateway | The gateway or next-hop IP address for this route. For overlay routes, this might be 'any' or a specific underlay IP. |
| Next Hop ID | The logical identifier of the next hop VeloCloud Edge or Gateway. |
| Dst LogicalId | The logical identifier of the destination VeloCloud Edge or Gateway. |
| Reachable | Indicates whether the destination is currently reachable (True/False). |
| Metric | A value used by routing protocols to determine the best path to a destination. Lower metrics are generally preferred. |
| Preference | A value indicating the trustworthiness or preference of the route source. Lower values are generally preferred. |
| Flags | Provides additional information about the route. Legend of the flag definitions is included in the bottom row of the output. |
| Vlan | The VLAN ID associated with this route, if applicable. |
| Intf | The interface associated with this route. |
| MTU | The Maximum Transmission Unit for the path associated with the destination interface of this route (will be `N/A` for overlay dc routes). |