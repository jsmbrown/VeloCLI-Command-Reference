#	--igmp_dump

##	Description
Dumps information related to the Internet Group Management Protocol (IGMP) status on the VeloCloud Edge. This includes details about multicast group memberships, interfaces, and timers. IGMP is used by hosts and adjacent routers on IPv4 networks to establish multicast group memberships.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --igmp_dump
show ip igmp groups
==================
Total IGMP groups: 0
Watermark warn limit(Not Set) : 0
Interface        Address         Group           Mode Timer    Srcs V Uptime
```

##  Field descriptions
The command output includes a summary followed by a table detailing IGMP group information.

**Summary Fields:**
| Field                     | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| Total IGMP groups         | The total number of active IGMP groups on the Edge.                         |
| Watermark warn limit      | The configured warning limit for the number of IGMP groups (if set).        |

**Table Columns:**
| Column    | Description                                                                      |
|-----------|----------------------------------------------------------------------------------|
| Interface | The network interface on which the IGMP group membership exists.                 |
| Address   | The IP address of the interface associated with the IGMP group.                    |
| Group     | The multicast IP address of the IGMP group.                                      |
| Mode      | The IGMP filter mode for the group (e.g., INCLUDE, EXCLUDE).                     |
| Timer     | The time remaining before the group membership expires or a query is sent.       |
| Srcs      | The number of sources for the multicast group (relevant for IGMPv3).             |
| V         | The IGMP version being used for this group (e.g., 1, 2, or 3).                   |
| Uptime    | The duration for which the Edge has been a member of this multicast group.       |