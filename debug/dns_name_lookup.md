# ` --dns_name_lookup HOSTNAME [v4 | v6 | all]`

## Description
This command queries the VeloCloud Edge's local DNS cache for a specified hostname and displays any cached IP address resolutions. It is useful for verifying DNS entries cached by the Edge, which can help in troubleshooting name resolution issues for traffic passing through the Edge.

## Arguments
| Argument   | Description                                                                                                                                                              |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `HOSTNAME` | (Mandatory) The hostname (e.g., `.velocloud.com`) to look up in the Edge's local DNS cache.                                                     |
| `v4`       | (Optional) If provided as the second argument after `HOSTNAME`, the command will display only cached IPv4 addresses for the specified `HOSTNAME`.                            |
| `v6`       | (Optional) If provided as the second argument after `HOSTNAME`, the command will display only cached IPv6 addresses for the specified `HOSTNAME`.                            |
| `all`      | (Optional) If provided as the second argument after `HOSTNAME`, the command will display both IPv4 and IPv6 cached addresses. This is the default behavior if this second argument is omitted. |

## Example usage
```
example_com:velocli> debug --dns_name_lookup .velocloud.net
[
  {
    "address": "104.18.41.185",
    "appid": 0,
    "name": ".velocloud.net",
    "ref_cnt": 0,
    "source": "DNS",
    "ttl": 273
  },
  {
    "address": "172.64.146.71",
    "appid": 0,
    "name": ".velocloud.net",
    "ref_cnt": 0,
    "source": "DNS",
    "ttl": 273
  }
]

```
## Field descriptions
| Column | Description |
|---|---|
| `address` | IP address cached for the provided hostname. |
| `appid` | Application ID associated with the provided hostname (`0` if hostname isn't mapped to an application definition) |
| `name` | FQDN of the cache entry |
| `source` | Source of the entry (either `DNS` for DNS snooping derived entries or `DPI` for DPI derived entries) |
| `ttl` | Remaining time to live in seconds for the associated cache entry |