#	--arp_dump

##	Description
Dumps the ARP cache for all active interfaces.

##  Arguments
None

##  Example usage
![image](Images/arp_dump.png)

##  Field descriptions
| Column | Description |
|---|---|
|Interface | Edge interface on which the ARP entry was learned. |
|Address | IP Address of the ARP entry |
|C-Tag | 802.1Q VLAN tag of host VLAN (0 if untagged) |
|MAC | MAC address of the host device |
|S-Tag | 802.1ad S-Tag of host (0 if untagged) |
|Source MAC | MAC address of the edge interface on which the ARP entry was learned |
