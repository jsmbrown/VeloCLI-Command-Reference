#	--vrrp_set_priority

##	Description
This command is used to set the Virtual Router Redundancy Protocol (VRRP) priority for a VeloCloud Edge when configured for High Availability (HA). The VRRP priority is a numerical value (typically ranging from 1 to 254, with 255 often reserved for the IP address owner and 0 for releasing mastership) that influences which Edge in an HA pair becomes the active (master) device. An Edge with a higher priority value is more likely to be elected as the master.

When this command is executed, the system will prompt the user to enter the desired priority value. The term `[priority]` in the functional description "set HA vrrp priority to [priority]" refers to this interactively entered value.

##  Arguments
| Argument | Description |
|---|---|
| (none) | This command does not accept arguments directly on the command line. It will prompt for the VRRP priority value after being invoked. |

##  Example usage
```
example_com:velocli> debug --vrrp_set_priority
```
Upon executing this command, the system will prompt the user to enter the VRRP priority. For example:
```
Enter VRRP priority: 150
```
If the user enters `150`, the command will attempt to set the Edge's VRRP priority for the relevant HA interface to 150.

##  Field descriptions
This command is used to modify a configuration setting and does not produce a tabular output with multiple fields. Output typically consists of a confirmation message indicating the success or failure of the operation. The new priority can be verified using HA status commands.