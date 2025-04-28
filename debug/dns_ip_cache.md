#	--dns_ip_cache [v4 | v6 | all]

##	Description
Dumps the contents of the FQDN to IP cache used for FQDN based business and firewall policies.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none (or 'all') | Display all cache entries |
| v4 | Display only IPv4 entries |
| v6 | Display only IPv6 entries |

##  Example usage
```
example_com:velocli> debug --dns_ip_cache v4
Total Cache Entries: 2
NAME                                 ADDRESS  TTL(s)  SOURCE  REFCNT
.gateway.example1.net      169.254.97.129       1     DNS       2
.example2.velocloud.net   169.254.224.129     81242   DPI       2
```

##  Field descriptions
| Column | Description |
|---|---|
| Name | FQDN of the entry |
| Address | IP address that the FQDN was observed resolving to |
| TTL(s) | Time to live in seconds for the cache entry (equal to the DNS TTL for DNS snooping based entries or 24 hours for DPI observed entries) |
| Source | Observation method used to derive the entry.  Value is "DNS" for entries derived from DNS snooping or "DPI" for entries observed via DPI |