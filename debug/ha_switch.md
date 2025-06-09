#	--ha_switch

##	Description
This command is used to manually switch the High Availability (HA) state of a VeloCloud Edge. If the Edge is currently in an ACTIVE HA state, executing this command will attempt to transition it to a STANDBY state, assuming a standby peer is available and healthy. This is typically used for maintenance or testing HA failover scenarios.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --ha_switch
[
  {
    "Result": "Invalid Request - Not Master"
  }
]
```
**Note:** The example output ` "Result": "Invalid Request - Not Master" ` indicates that the command was issued on an Edge that was already in a STANDBY state or was not part of an HA pair. If the command were successful on an ACTIVE Edge, the Edge would transition to STANDBY, and its HA peer would become ACTIVE. The specific output for a successful switch can vary but generally indicates the state change.

##  Field descriptions
| Field  | Description                                                                                                |
|--------|------------------------------------------------------------------------------------------------------------|
| Result | Indicates the outcome of the command. "Invalid Request - Not Master" means the Edge was not in an ACTIVE HA state. A successful execution would typically result in a message confirming the HA state switch. |