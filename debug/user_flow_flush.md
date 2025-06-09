#	--user_flow_flush `[all | src-ip]` `[all | dest-ip]`

##	Description
This command allows a user to flush entries from the current flow table. This can be useful for troubleshooting or clearing stale flow information.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` (first argument) | Flushes all flows regardless of source IP address. This is the default if no source IP is specified. |
| `src-ip` | Specifies the source IP address. Only flows matching this source IP will be considered for flushing. |
| `all` (second argument) | Flushes all flows (that matched the first argument) regardless of destination IP address. This is the default if no destination IP is specified. |
| `dest-ip` | Specifies the destination IP address. Only flows matching this destination IP (and the source IP criteria) will be flushed. |

##  Example usage
To flush all user flow entries:
```
example_com:velocli> debug --user_flow_flush
```
To flush user flow entries for a specific source IP address:
```
example_com:velocli> debug --user_flow_flush 192.168.1.10
```
To flush user flow entries for a specific source and destination IP address:
```
example_com:velocli> debug --user_flow_flush 192.168.1.10 8.8.8.8
```