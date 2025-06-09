#	--pd6_dump

##	Description
Displays the contents of the DHCPv6 Prefix Delegation (PD) hash table. This table contains information about IPv6 prefixes delegated to the VeloCloud Edge's WAN interfaces and subsequently used or advertised on its LAN interfaces. This command is useful for troubleshooting IPv6 address assignment and routing when using DHCPv6 Prefix Delegation.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --pd6_dump
Tag   WAN interface  Delegated Prefixes  LAN interfaces  LAN IPv6 Address  Prefixes Advertised

example_com:velocli>
```
*(Note: The example output above shows the headers but no data. In a live environment with active DHCPv6 PD, entries would be listed below these headers.)*

##  Field descriptions
| Column | Description |
|---|---|
| Tag | An internal identifier or tag for the DHCPv6 Prefix Delegation entry. |
| WAN interface | The WAN interface on the VeloCloud Edge that received the IPv6 prefix delegation from an upstream DHCPv6 server (e.g., ISP router). |
| Delegated Prefixes | The IPv6 prefix(es) delegated by the upstream DHCPv6 server to this Edge's WAN interface. |
| LAN interfaces | The LAN interface(s) on the VeloCloud Edge that are utilizing or advertising sub-prefixes from the delegated prefix pool. |
| LAN IPv6 Address | The specific IPv6 address assigned to the LAN interface, typically derived from the delegated prefix. |
| Prefixes Advertised | The IPv6 prefixes that the Edge is advertising on its LAN segments, derived from the delegated prefixes, for use by downstream clients. |