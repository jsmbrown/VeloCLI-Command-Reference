#	--clear_arp_cache [IFNAME]

##	Description
Clears the ARP (Address Resolution Protocol) cache on the VeloCloud Edge. This can be useful for troubleshooting network connectivity issues where incorrect or stale ARP entries might be causing problems.

##  Arguments (optional)
| Argument | Description |
|---|---|
| IFNAME | Specifies the interface name (e.g., GE1, GE2, SFP1) for which the ARP cache should be cleared. If this argument is omitted, the ARP cache for all interfaces on the Edge will be cleared. |

##  Example usage
To clear the ARP cache for all interfaces:
```
example_com:velocli> debug --clear_arp_cache
```

To clear the ARP cache for a specific interface (e.g., GE1):
```
example_com:velocli> debug --clear_arp_cache GE1
```

##  Field descriptions
This command does not produce tabular output. It typically returns a confirmation message if successful or an error message if it fails.