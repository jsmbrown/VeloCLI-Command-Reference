# --vrrp_startup

## Description
Starts the High Availability (HA) Virtual Router Redundancy Protocol (VRRP) service on the VeloCloud Edge. This command is used to initiate the VRRP processes, enabling the Edge to participate in an HA configuration. In an HA setup, VRRP allows for automatic failover to a standby Edge if the active Edge becomes unavailable, ensuring network continuity for LAN-side devices.

## Arguments
This command does not accept any arguments.

## Example usage
```
example_com:velocli> debug --vrrp_startup
[]

example_com:velocli>
```

## Field descriptions
This command does not return any specific fields in its output. The `[]` typically indicates that the command to start the VRRP service has been accepted by the system. Further status on VRRP operation can usually be found in system logs or dedicated HA status commands.