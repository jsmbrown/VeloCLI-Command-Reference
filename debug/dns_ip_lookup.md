#	--dns_ip_lookup &lt;IP_ADDRESS&gt;

##	Description
Queries the VeloCloud Edge's internal DNS IP cache to find the hostname associated with a given IP address. This cache is typically populated by the Edge through mechanisms like DNS snooping (observing DNS responses on the LAN) or other DNS resolution processes. This command is useful for troubleshooting name resolution issues or verifying the Edge's understanding of local network hosts.

##  Arguments
| Argument | Description |
|---|---|
| `IP_ADDRESS` | The IP address for which to look up the corresponding hostname in the DNS IP cache. This must be a valid IPv4 or IPv6 address. |

##  Example usage
```
example_com:velocli> debug --dns_ip_lookup 8.8.8.8
IP: 8.8.8.8, Hostname: dns.google, TTL: 287, Source: DNS_SNOOPING
```
**Note:** If the `IP_ADDRESS` argument is omitted, the command will display usage information for the `debug` utility, as shown in the input description. A successful lookup requires specifying an IP address.

If an IP address is not found in the cache, the output might look like:
```
example_com:velocli> debug --dns_ip_lookup 192.0.2.1
IP: 192.0.2.1, Hostname: Not Found
```

##  Field descriptions
| Column   | Description |
|----------|-------------|
| IP       | The IP address that was queried in the DNS IP cache. |
| Hostname | The hostname associated with the queried IP address. If no entry is found, this may display "Not Found" or a similar indicator. |
| TTL      | Time To Live (in seconds). This indicates how long the cache entry is considered valid. This field may not be present if the hostname is not found or if TTL is not applicable. |
| Source   | The method by which the Edge learned this IP-to-hostname mapping (e.g., `DNS_SNOOPING`, `STATIC`, `DHCP`). This field may not be present if the hostname is not found. |