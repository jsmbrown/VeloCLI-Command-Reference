#	--clear_nd6_cache <IFNAME>

##	Description
Clears the IPv6 Neighbor Discovery (ND6) cache on the VeloCloud Edge. The ND6 cache stores mappings between IPv6 addresses and their corresponding link-layer (MAC) addresses for neighbors on the same link. Clearing this cache can be essential for troubleshooting IPv6 connectivity issues, such as when a neighbor's MAC address changes or an entry becomes stale, by forcing the Edge to re-initiate the neighbor discovery process for the specified interface.

##  Arguments
| Argument | Description |
|---|---|
| IFNAME | Specifies the interface name (e.g., `GE1`, `GE2`, `eth0`) for which the ND6 cache should be cleared. This argument is mandatory. The example usage below shows the help output, which may occur if this mandatory argument is not provided. |

##  Example usage
```
example_com:velocli> debug --clear_nd6_cache GE2
{
  "INFO": "ND6 Cache cleaned up"
}
```

##  Field descriptions
Output of this command is either a confirmation that ND6 cache is cleared, or, an error message if a valid interface isn't specified.