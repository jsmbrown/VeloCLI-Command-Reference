#	--dns_ip_cache_update_ttl <IP ADDRESS> <TTL>

##	Description
Updates the Time-To-Live (TTL) for a specific IP address in the VeloCloud Edge's local DNS IP cache. This command allows an administrator to manually adjust how long the Edge will cache the mapping for a particular IP address before it needs to be refreshed. Modifying TTL values can be useful for managing how quickly the Edge adapts to changes in network services associated with an IP address or for troubleshooting DNS-related issues.

##  Arguments
| Argument      | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `<IP ADDRESS>`  | **Required.** The IP address (e.g., `192.168.1.100` or `2001:db8::1`) for which the DNS cache TTL needs to be updated. |
| `<TTL>`         | **Required.** The new Time-To-Live value in seconds for the DNS cache entry of the specified IP address. This should be a non-negative integer (e.g., `300` for 5 minutes, `0` to potentially force an immediate refresh on next lookup). |

##  Example usage
To update the TTL for the IP address `8.8.8.8` in the DNS IP cache to 600 seconds:
```
example_com:velocli> debug --dns_ip_cache_update_ttl 8.8.8.8 600
```
Upon successful execution, this command typically modifies the internal cache entry and may not produce any specific output, or it might return a simple confirmation.

If the command is entered without the required `<IP ADDRESS>` and `<TTL>` arguments, the system will display usage instructions for the `debug.py` script, as illustrated by the example output provided in the problem description:
```
example_com:velocli> debug --dns_ip_cache_update_ttl
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##  Field descriptions
This command does not produce tabular output. Its primary function is to modify an internal configuration value—the TTL of a specific entry within the Edge's DNS IP cache.