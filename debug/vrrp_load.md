#	--vrrp_load

##	Description
Reloads the VRRP (Virtual Router Redundancy Protocol) configuration file. This command is used to apply or refresh High Availability (HA) settings managed by VRRP on the VeloCloud Edge. VRRP allows for router redundancy, ensuring network uptime in case of a device failure.

##  Arguments (optional)
This command does not accept any arguments.

##  Example usage
```
example_com:velocli> debug --vrrp_load
[
  {
    "instanceProcessed": 0,
    "totalActiveInstance": 0
  }
]
```

##  Field descriptions
The output is a JSON array containing an object with the following fields:

| Field                 | Description                                                                                                |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| `instanceProcessed`   | Indicates the number of VRRP instances that were successfully processed from the configuration file when the command was executed. |
| `totalActiveInstance` | Shows the total count of VRRP instances that are currently active and operational on the Edge.             |