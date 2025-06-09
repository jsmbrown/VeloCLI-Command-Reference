#	--self_ip_dump [v4 | v6 | all]

##	Description
This command displays the IP addresses configured on the VeloCloud Edge itself. These are the "self" IP addresses used by the appliance for its various interfaces and functions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4       | Display only IPv4 self IP addresses. |
| v6       | Display only IPv6 self IP addresses. |
| all      | Display all self IP addresses (both IPv4 and IPv6). This is typically the default behavior if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --self_ip_dump
```
*(Note: The output format for this command was not provided in the example. It would typically list IP addresses, associated interfaces, and potentially other relevant details.)*

##  Field descriptions
| Column | Description |
|---|---|
|   | *(Output fields for this command are not detailed in the provided example.)* |