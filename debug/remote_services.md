#	--remote_services

##	Description
Displays a list of IP addresses for remote services that the VeloCloud Edge is permitted to communicate with. These services are typically configured via the VeloCloud Orchestrator and can include management, control, or data plane related services essential for the SD-WAN functionality.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --remote_services
[
  {
    "allowed_ips": [
      {
        "remote_ip": "216.221.27.88"
      }
    ]
  }
]
```

##  Field descriptions
| Field | Description |
|---|---|
| `allowed_ips` | An array containing objects, where each object specifies an allowed remote IP address. This structure allows for a list of multiple permitted IPs. |
| `remote_ip` | The specific IP address of a remote service that the Edge is configured to trust or interact with. This could be an IP address for the VeloCloud Orchestrator, VeloCloud Gateways, or other critical infrastructure components. |