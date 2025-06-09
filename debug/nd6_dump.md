#	--nd6_dump [Number of entries]

##	Description
Dump the IPv6 Neighbor Discovery (ND) cache for active interfaces. The ND6 cache stores information about IPv6 neighbors, including their link-layer addresses, reachability state, and whether they are routers. This command is useful for troubleshooting IPv6 connectivity issues.

##  Arguments (optional)
| Argument | Description |
|---|---|
| Number of entries | Specifies the maximum number of ND6 cache entries to display. If not specified, all entries are displayed. |

##  Example usage
```
example_com:velocli> debug --nd6_dump
Interface   Address  C-Tag  S-Tag  Mac  State  Router  Queue  Age(Sec)  Last Rcv(Sec)  Refcnt

```
##  Field descriptions
| Column | Description |
|---|---|
| Interface | The network interface on which the neighbor was discovered. |
| Address | The IPv6 address of the neighbor. |
| C-Tag | Customer VLAN tag. |
| S-Tag | Service VLAN tag. |
| Mac | The MAC address (link-layer address) of the neighbor. |
| State | The state of the neighbor cache entry (e.g., INCOMPLETE, REACHABLE, STALE, DELAY, PROBE). |
| Router | Indicates if the neighbor is an IPv6 router (Yes/No or True/False). |
| Queue | The number of packets queued for transmission to this neighbor. |
| Age(Sec) | The age of the cache entry in seconds. |
| Last Rcv(Sec) | Time in seconds since the last Neighbor Advertisement or other reachability confirmation was received from this neighbor. |
| Refcnt | Reference count for the cache entry. |