#	--bfd_local_ip_dump `[all|prefix]` `[all|segment-id]`

##	Description
Dumps the list of local IP addresses configured for BFD (Bidirectional Forwarding Detection) sessions on the VeloCloud Edge. BFD is used to provide fast failure detection for routing protocols and paths. This command helps in verifying which local IP addresses are sourced for BFD packets.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` or `prefix` | Filters the output by a specific IP prefix. If `all` or no argument is provided, all BFD local IPs are displayed. |
| `all` or `segment-id` | Filters the output by a specific segment ID. If `all` or no argument is provided, BFD local IPs across all relevant segments are displayed. |

##  Example usage
```
example_com:velocli> debug --bfd_local_ip_dump
```
*(Note: The example usage provided does not include sample output for this command. The output would typically list IP addresses and potentially associated segment or interface information.)*

##  Field descriptions
| Column | Description |
|---|---|
| *(N/A)* | *(Output format and specific fields are not detailed in the provided example. Output would typically include local IP addresses used for BFD.)* |