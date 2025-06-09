#	--dpdk_bond_dump [interface physical name]

##	Description
Dump DPDK (Data Plane Development Kit) bond information. This command is used to display details about link bonding configurations and status for interfaces managed by DPDK. Link bonding combines multiple network interfaces into a single logical interface to provide increased bandwidth or redundancy.

##  Arguments (optional)
| Argument                | Description                                                                                                                               |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| interface physical name | Specifies the physical name of the DPDK bonded interface (e.g., `bond0`) or a member interface for which to display bonding information. If omitted, information for all DPDK bonded interfaces may be displayed. |

##  Example usage
```
example_com:velocli> debug --dpdk_bond_dump
```
**(Note: The output of this command is not provided in the example. The output would typically include details about bonded interfaces, their modes, member links, status, and statistics.)**

##  Field descriptions
| Column | Description |
|---|---|
|   | *(Output structure and specific fields for this command are not available in the provided example. Generally, this would describe columns like Interface Name, Mode, Active Slaves, Slave Interface, Status, etc.)* |