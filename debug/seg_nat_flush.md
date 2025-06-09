#	--seg_nat_flush &lt;app_name&gt;

##	Description
Flush all entries of the designated app in the segment NAT table.

##  Arguments
| Argument   | Description                                                                                                                               |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `<app_name>` | **Required.** Specifies the application whose NAT entries will be flushed from the segment NAT table. Must be one of the following values: `RSYSLOG`, `SNMP`, `ANALYTICS`, `TACACS`. |

##  Example usage
```
example_com:velocli> debug --seg_nat_flush RSYSLOG
```