#	--link_stats `[v4 | v6 | all]` `[up | all]`

##	Description
Displays current statistics for all WAN links configured on the VeloCloud Edge. This includes information about the link's configuration, state, addressing, and traffic counters.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Show statistics for IPv4 links only. |
| `v6` | Show statistics for IPv6 links only. |
| `all` (default for IP version) | Show statistics for both IPv4 and IPv6 links. |
| `up` | Show statistics for links that are currently in an 'UP' state. |
| `all` (default for link state) | Show statistics for all links regardless of their state. |

##  Example usage
```
example_com:velocli> debug --link_stats
Name        Interface          Overlay  VLAN  prio8021P    Mode   Type   MTU  Backup  LocalIpAddr  PublicIpAddr  LogicalId                     InternalLogicalId  LinkMode    State  VPN State  bandwidthKbpsTx  bandwidthKbpsRx  BytesTx   BytesRx
Microsoft         GE1  AUTO DISCOVERED  NONE       NONE  PUBLIC  WIRED  1500   FALSE   172.30.0.6                           00000001-3913-4132-bca0-dd18bdf45da5    ACTIVE  INITIAL       DEAD              0.0              0.0  4446941  38810922
```

##  Field descriptions
| Column | Description |
|---|---|
| Name | The user-defined name of the WAN link as configured in the VeloCloud Orchestrator. |
| Interface | The physical or logical interface associated with the WAN link (e.g., GE1, GE2, SFP1, PPPoE0). |
| Overlay | Indicates how the link's overlay characteristics (e.g., IP address) are determined. `AUTO DISCOVERED` means the system automatically detects these. |
| VLAN | The VLAN ID tagged on this link, if any. `NONE` indicates no VLAN tagging. |
| prio8021P | The 802.1p CoS (Class of Service) priority value set for this link. `NONE` indicates no specific 802.1p priority. |
| Mode | Indicates if the link is `PUBLIC` (connected to the internet) or `PRIVATE` (e.g., MPLS). |
| Type | The physical type of the link, such as `WIRED` or `WIRELESS`. |
| MTU | Maximum Transmission Unit size for the link in bytes. |
| Backup | Indicates if the link is configured as a backup link (`TRUE` or `FALSE`). |
| LocalIpAddr | The local IP address assigned to the Edge's interface for this link. |
| PublicIpAddr | The public IP address detected for this link, often the address after NAT. May be blank if not applicable or not yet discovered. |
| LogicalId | A unique identifier assigned by the VeloCloud system to this specific WAN link. |
| InternalLogicalId | An internal unique identifier for the link. |
| LinkMode | The operational mode of the link, typically `ACTIVE`. Can also be `STANDBY` for backup links. |
| State | The current physical or L2 operational state of the link (e.g., `INITIAL`, `UP`, `DOWN`, `DISCONNECTED`). |
| VPN State | The state of the VeloCloud VPN tunnel (path) over this link (e.g., `DEAD`, `STABLE`, `UNSTABLE`, `UP`). |
| bandwidthKbpsTx | The measured or configured transmit bandwidth for the link in Kilobits per second. |
| bandwidthKbpsRx | The measured or configured receive bandwidth for the link in Kilobits per second. |
| BytesTx | The total number of bytes transmitted over this link since the last counter reset or reboot. |
| BytesRx | The total number of bytes received over this link since the last counter reset or reboot. |