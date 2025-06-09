#	--dns_name_cache [v4 | v6 | all]

##	Description
Displays the contents of the DNS domain name cache on the VeloCloud Edge. This cache stores recently resolved domain names and their corresponding IP addresses to speed up subsequent lookups and is used for various functions, including connecting to VeloCloud infrastructure, Cloud Security Services (CSS), or other network destinations.

##	Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Display only DNS cache entries with IPv4 addresses. |
| `v6` | Display only DNS cache entries with IPv6 addresses. |
| `all` | Display all DNS cache entries (both IPv4 and IPv6). This is the default behavior if no argument is specified. |

##	Example usage
```
example_com:velocli> debug --dns_name_cache
Total Cache Entries: 5
NAME                                 ADDRESS  TTL(s)  SOURCE  APPMAP APPID
.veco12-kiad1.velocloud.net   152.65.224.129      13     DNS             0
.gateway.zscalerthree.net      165.225.34.43     -33     DNS             0
.gateway.zscalerthree.net     165.225.216.34      87     DNS             0
.gateway.zscalerthree.net      170.85.15.129     104     DNS             0
```

##	Field descriptions
| Column | Description |
|---|---|
| `NAME` | The fully qualified domain name (FQDN) that was resolved and cached. |
| `ADDRESS` | The IP address (IPv4 or IPv6) resolved for the FQDN. |
| `TTL(s)` | The remaining Time To Live for this DNS cache entry, in seconds. This indicates how long the entry will remain valid in the cache before requiring a fresh lookup. |
| `SOURCE` | The method or protocol through which the DNS information was obtained (e.g., "DNS" for a standard DNS query). |
| `APPMAP APPID` | The Application ID associated with the domain name, if identified by the Edge's application mapping feature. A '0' typically indicates no specific application is mapped or it's a generic infrastructure entry. |