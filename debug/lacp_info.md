#	--lacp_info

##	Description
Shows LACP configuration and protocol status details

##  Arguments (optional)
| Argument | Description |
|---|---|
| none (or 'all') | Display LACP bundles |
| [interface name] | Display only the specified LAG|

```
example_com:velocli> debug --lacp_info
LAG Interface      LAG Status  Slave Port  Actor Status  Partner Status
LAG1                       UP         GE4            UP              UP
                                      GE8            UP              UP
LAG2                       UP         GE6            UP              UP
                                      GE7            UP              UP
```

##  Field descriptions
| Column | Description |
|---|---|
| LAG Interface | Logical interface name of the LACP bundle |
| LAG Status | Protocol up/down status of the LAG |
| Slave Port | Physical interfaces included in the LAG |
| Actor Status | Local interface status of the slave port |
| Partner Status | LACP peer's interface status of the slave port |
