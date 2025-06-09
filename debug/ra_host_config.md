#	--ra_host_config

##	Description
Displays the Router Advertisement (RA) host configurations for each interface on the VeloCloud Edge. This command shows whether an interface is configured to accept specific parameters (like MTU, default routes, specific routes, and timers) from RAs sent by routers on the network. This is relevant for IPv6 stateless address autoconfiguration (SLAAC).

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --ra_host_config
Interface   AcceptMTU  AcceptDefaultRoutes  AcceptSpecificRoutes  AcceptTimers
GE1              True                 True                  True          True
GE2              True                 True                  True          True
```

##  Field descriptions
| Column | Description |
|---|---|
| Interface | The identifier of the network interface on the Edge (e.g., GE1, GE2). |
| AcceptMTU | Indicates whether the interface is configured to accept Maximum Transmission Unit (MTU) information from received Router Advertisements. `True` means it accepts; `False` means it does not. |
| AcceptDefaultRoutes | Indicates whether the interface is configured to accept default route information from received Router Advertisements. `True` means it accepts; `False` means it does not. |
| AcceptSpecificRoutes | Indicates whether the interface is configured to accept more specific route information (prefix information options) from received Router Advertisements. `True` means it accepts; `False` means it does not. |
| AcceptTimers | Indicates whether the interface is configured to accept router lifetime and other timer values from received Router Advertisements. `True` means it accepts; `False` means it does not. |