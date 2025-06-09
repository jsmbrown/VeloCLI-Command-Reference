#	--dce_edge [v4 | v6 | all]

##	Description
Displays a list of Dynamic Cost Edges (DCE) whose information has been pushed to the local VeloCloud Edge from a VeloCloud Gateway (VCG). This information is used in path selection and dynamic tunnel establishment.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Display only IPv4 address information for the DCE edges. |
| `v6` | Display only IPv6 address information for the DCE edges. |
| `all` | Display both IPv4 and IPv6 address information (if available) for the DCE edges. This is the default behavior if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --dce_edge
DCE LogicalId   V4 Address  V6 Address  Peer Tun Pref  Private  Type  VCMP Port  IKE Port  NAT-t Port  MPLS Network

example_com:velocli>
```

##  Field descriptions
| Column | Description |
|---|---|
| DCE LogicalId | The unique logical identifier of the remote DCE. |
| V4 Address | The IPv4 address of the remote DCE. |
| V6 Address | The IPv6 address of the remote DCE. |
| Peer Tun Pref | Peer Tunnel Preference. Indicates the preference level for establishing tunnels to this peer. |
| Private | Indicates if the DCE is on a private network or uses private IP addressing. |
| Type | The type or role of the DCE (e.g., Spoke, Hub). |
| VCMP Port | The VeloCloud Management Protocol (VCMP) port number used by the DCE for management communications. |
| IKE Port | The Internet Key Exchange (IKE) port number (typically UDP 500) used by the DCE for establishing IPSec tunnels. |
| NAT-t Port | The NAT Traversal port number (typically UDP 4500) used by the DCE for IPSec tunnels when Network Address Translation (NAT) is detected. |
| MPLS Network | Identifier or information related to an MPLS network associated with the DCE, if applicable. |