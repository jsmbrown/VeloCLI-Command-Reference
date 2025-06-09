# ` --dns_name_lookup HOSTNAME [v4 | v6 | all]`

## Description
This command queries the VeloCloud Edge's local DNS cache for a specified hostname and displays any cached IP address resolutions. It is useful for verifying DNS entries cached by the Edge, which can help in troubleshooting name resolution issues for traffic passing through the Edge.

## Arguments
| Argument   | Description                                                                                                                                                              |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `HOSTNAME` | (Mandatory) The hostname (e.g., `www.velocloud.com`, `portal.sase.vmware.com`) to look up in the Edge's local DNS cache.                                                     |
| `v4`       | (Optional) If provided as the second argument after `HOSTNAME`, the command will display only cached IPv4 addresses for the specified `HOSTNAME`.                            |
| `v6`       | (Optional) If provided as the second argument after `HOSTNAME`, the command will display only cached IPv6 addresses for the specified `HOSTNAME`.                            |
| `all`      | (Optional) If provided as the second argument after `HOSTNAME`, the command will display both IPv4 and IPv6 cached addresses. This is typically the default behavior if this second argument is omitted. |

## Example usage
The command requires a `HOSTNAME` as its first argument. If this mandatory argument is not provided, the system will display usage instructions, as shown below:
```
example_com:velocli> debug --dns_name_lookup
Usage: debug.py --dns_name_lookup HOSTNAME [v4 | v6 | all]

example_com:velocli>
```
**Hypothetical successful execution:**
To look up IPv4 addresses for `www.velocloud.com`:
```
example_com:velocli> debug --dns_name_lookup www.velocloud.com v4
```
*(Note: The exact output format for a successful command is not provided in the input. It would typically list the cached IP addresses and their TTLs.)*

## Field descriptions
| Column | Description |
|---|---|
|   |  *Specific output fields for a successful command execution are not detailed in the provided example. A successful lookup would typically display the hostname queried, followed by any cached IP address(es) (IPv4 and/or IPv6 depending on the arguments used) and potentially their remaining Time-To-Live (TTL) in the cache.* |