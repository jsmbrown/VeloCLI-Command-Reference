#	--ha_reset_failover

##	Description
In a VeloCloud Edge High Availability (HA) deployment, this command resets the failover timer to its original configured value. This timer dictates how quickly the standby Edge takes over if the active Edge becomes unresponsive. Resetting it ensures the HA pair adheres to its standard failover parameters, which might have been temporarily altered for maintenance or testing purposes.

##	Arguments
This command does not take any arguments.

##	Example usage
```
example_com:velocli> debug --ha_reset_failover
example_com:velocli>
```

##	Field descriptions
This command does not produce tabular output with specific fields. It executes an action to reset the HA failover time and, upon successful completion, returns to the command prompt.