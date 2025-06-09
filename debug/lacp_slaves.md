#	--lacp_slaves [all|<iface_name>]

##	Description
Displays the active slave interfaces for Link Aggregation Control Protocol (LACP) groups configured on the VeloCloud Edge. LACP allows multiple physical network interfaces to be bundled together to form a single logical channel, increasing bandwidth and providing redundancy. This command helps identify which member interfaces are currently participating in a given LACP bundle.

##  Arguments (optional)
| Argument | Description |
|---|---|
| all | Displays active slave interfaces for all configured LACP groups. This is the default behavior if no argument is specified. |
| `<iface_name>` | Specifies the name of a particular LACP interface (e.g., LAG0, LAG1) for which to display active slave interfaces. |

##  Example usage
```
example_com:velocli> debug --lacp_slaves
LAG-Interface   Active-Slaves

example_com:velocli>
```
```
example_com:velocli> debug --lacp_slaves LAG0
LAG-Interface   Active-Slaves
LAG0            GE1,GE2
```

##  Field descriptions
| Column | Description |
|---|---|
| LAG-Interface | The name of the Link Aggregation Group (LAG) interface. |
| Active-Slaves | A comma-separated list of physical member interfaces that are currently active and participating in the specified LAG-Interface. |