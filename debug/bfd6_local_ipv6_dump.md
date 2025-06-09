#	--bfd6_local_ipv6_dump [all | prefix] [all | segment-id]

##	Description
Dumps the list of local IPv6 addresses configured for Bidirectional Forwarding Detection (BFD6) monitoring on the VeloCloud Edge. BFD is a network protocol used to detect faults between two forwarding engines.

##  Arguments (optional)
The command accepts two optional positional arguments. If arguments are omitted, the command typically defaults to showing all entries.

| Argument     | Description                                                                                                |
|--------------|------------------------------------------------------------------------------------------------------------|
| `none`       | If no arguments are provided, the command displays all BFD6 local IPv6 entries across all segments.        |
| `all`        | Keyword. When used as the first argument, it refers to all prefixes. When used as the second argument, it refers to all segments. |
| `prefix`     | Specifies an IPv6 prefix (e.g., `2001:db8:abcd::/64`) to filter the list. This is the first argument.        |
| `segment-id` | Specifies a numerical segment ID to filter the list. This is the second argument.                          |

##  Example usage
```
example_com:velocli> debug --bfd6_local_ipv6_dump
```
*(Note: The example above shows the command invocation. Actual output for this command is not provided in the input material.)*

##  Field descriptions
| Column | Description |
|---|---|
|   |   |
*(Note: Specific field descriptions for the output of this command are not available as no sample output was provided.)*