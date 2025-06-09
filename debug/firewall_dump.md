#	--firewall_dump `[all | segment-id]` `[v4 | v6 | all]`

##	Description
This command displays the current firewall version and the status of various firewall policies and features on the VeloCloud Edge. It provides a snapshot of the security posture enforced by the Edge's firewall.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no segment-id is specified) Show firewall information for all segments. |
| `segment-id` | Specify a particular segment ID to display firewall information for that segment. |
| `v4` | Display IPv4 firewall information. |
| `v6` | Display IPv6 firewall information. |
| `all` | (Default if no IP version is specified) Display firewall information for all IP versions (IPv4 and IPv6). |

##  Example usage
```
example_com:velocli> debug --firewall_dump

Stateful Firewall : Enabled
EFS Status : Enabled
URL Filtering : Enabled
Malicious IP Filtering : Enabled
IDPS : Enabled
```

##  Field descriptions
| Field | Description |
|---|---|
| Stateful Firewall | Indicates whether the stateful firewall functionality is enabled or disabled. |
| EFS Status | Indicates the status of Edge Firewall Services (EFS). This could relate to advanced firewall features or integrations. |
| URL Filtering | Indicates whether URL filtering, which blocks access to websites based on their URLs, is enabled or disabled. |
| Malicious IP Filtering | Indicates whether filtering based on known malicious IP addresses is enabled or disabled. |
| IDPS | Indicates whether the Intrusion Detection and Prevention System (IDPS) is enabled or disabled. |