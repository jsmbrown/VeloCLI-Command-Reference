#	--debug_path_uptime

##	Description
This command dumps the internal path uptime hash table. This table tracks the uptime statistics for various paths established by the VeloCloud Edge. This information can be useful for diagnosing path stability and performance issues.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --debug_path_uptime
[]
```

##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example output `[]` indicates an empty hash table or that no specific fields are displayed in this summarized view. Detailed path uptime information is typically viewed through the VeloCloud Orchestrator or more specific path diagnostic commands. |