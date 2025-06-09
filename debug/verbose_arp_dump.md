#	--verbose_arp_dump [Number of entries]

##	Description
Dumps the ARP (Address Resolution Protocol) cache for active interfaces on the VeloCloud Edge. This command lists ARP entries, which map IP addresses to MAC addresses for devices on the local network segments connected to the Edge's interfaces. The output can be configured to show all entries or a limited number per interface.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `Number of entries` | Specifies the maximum number of ARP entries to display for each interface. If this argument is omitted, or if `0` is provided, all ARP entries for each active interface will be displayed. |

##  Example usage
```
example_com:velocli> debug --verbose_arp_dump
[
  {
    "interface": "GE1",
    "snmp_if_index": 16777216,
    "table": [
      {
```

##  Field descriptions
The command output is a JSON array. Each element in the array is an object representing an active interface on the VeloCloud Edge and its associated ARP table entries.

| Field | Description |
|---|---|
| `interface` | String. The name of the network interface (e.g., "GE1", "GE2"). This indicates the interface for which the ARP entries are being listed. |
| `snmp_if_index` | Integer. The SNMP (Simple Network Management Protocol) interface index associated with this network interface. This is a unique identifier for the interface often used in network management systems. |
| `table` | Array of Objects. This array contains the ARP entries discovered or configured on the respective `interface`. Each object within this array represents a single ARP entry. The example output is truncated before showing the specific fields of an ARP entry object. Typically, these objects would contain details such as: <br> - **IP Address**: The Layer 3 IP address that has been resolved. <br> - **MAC Address**: The Layer 2 MAC (Media Access Control) address corresponding to the IP address. <br> - **State**: The current state of the ARP entry (e.g., REACHABLE, STALE, INCOMPLETE, PERMANENT). <br> - **Age**: The duration (often in seconds) for which the entry has been in the cache or the time remaining until it expires (for dynamic entries). <br> - **Type**: Indicates if the ARP entry is dynamic (learned) or static (manually configured). |