#	--ospf_sync_list [all | v4 | v6]

##	Description
Displays entries from the OSPF (Open Shortest Path First) synchronization view on the VeloCloud Edge. This command is used to inspect the state of OSPF routes that are being learned from or advertised to OSPF neighbors, typically for integrating the SD-WAN overlay with existing underlay networks or LAN segments. OSPF is a standards-based interior gateway protocol (IGP) used to distribute routing information within a single autonomous system.

##	Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no argument is specified) Displays all OSPF synchronization entries, for both IPv4 and IPv6. |
| `v4` | Displays only IPv4 OSPF synchronization entries. |
| `v6` | Displays only IPv6 OSPF synchronization entries. |

##	Example usage
```
example_com:velocli> debug --ospf_sync_list
Address   Netmask  Nbr IP  Intf  Synced  Sync_Action

example_com:velocli>
```
**(Note: The example output above shows the headers. Actual output would list OSPF synchronization entries below these headers, detailing specific routes and their synchronization status.)**

##	Field descriptions
| Column | Description |
|---|---|
| Address | The network address of the OSPF route. |
| Netmask | The subnet mask for the network address. |
| Nbr IP | The IP address of the OSPF neighbor from which this route information was learned or to which it is being advertised. |
| Intf | The interface on the VeloCloud Edge involved in this OSPF synchronization (e.g., GE1, GE2). |
| Synced | Indicates the synchronization status of the OSPF entry (e.g., True, False, or a specific state reflecting whether the route has been successfully processed and integrated). |
| Sync_Action | Describes the action taken or pending for synchronization with the VeloCloud SD-WAN routing table (e.g., Add, Delete, Update, No Action). |