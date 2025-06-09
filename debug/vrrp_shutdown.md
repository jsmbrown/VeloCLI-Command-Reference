#	--vrrp_shutdown

##	Description
Stops the Virtual Router Redundancy Protocol (VRRP) process on the VeloCloud Edge. VRRP is a standard protocol used to provide High Availability (HA) by allowing two Edges to share a virtual IP address, with one acting as Master and the other as Backup. Executing this command will manually cease VRRP operations on the Edge. This action may cause the Edge to relinquish its Master role if it is currently the active Master, or to stop participating in VRRP elections if it is in a Backup state. This command is typically used for planned maintenance, troubleshooting HA issues, or to intentionally force a failover to the standby Edge in an HA pair.

##  Arguments
This command does not accept any arguments.

##  Example usage
```
example_com:velocli> debug --vrrp_shutdown
[]

example_com:velocli>
```

##  Field Descriptions
The command returns an empty array `[]` upon successful execution. This indicates that the request to stop the VRRP process on the Edge has been accepted and processed. No specific data fields are returned in the output for this command.