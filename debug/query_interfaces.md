#	--query_interfaces

##	Description
This command instructs the VeloCloud Edge to query the underlying operating system (kernel) for information about its network interfaces. This is typically used for diagnostic purposes to ensure the Edge's understanding of the network interfaces aligns with the system's view. The result indicates that the query will be processed asynchronously within 60 seconds.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##  Example usage
```
example_com:velocli> debug --query_interfaces
{"result": "Interface will be queried within 60 seconds"}

example_com:velocli>
```
##  Field descriptions
| Column | Description |
|---|---|
| result |  Indicates the status of the command. In this case, it confirms that the interface query will be performed within the next 60 seconds. |