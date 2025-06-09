#	--radius_on_routed

##	Description
This command dumps debugging information related to RADIUS (Remote Authentication Dial-In User Service) authentication specifically for clients connected to routed interfaces on the VeloCloud Edge. This is useful for troubleshooting authentication issues for devices that are not on directly connected LAN segments but are routed through the Edge.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --radius_on_routed
====================== MAC Bypass Rules ====================
iface   MAC  Hits
====================== Known Clients ====================
iface   MAC  Age(ms)  Last Check(ms)  Flags  Hits

```

##  Field descriptions
The output is divided into two sections:

### MAC Bypass Rules
This section lists the MAC addresses that are configured to bypass RADIUS authentication on routed interfaces.

| Column | Description |
|---|---|
| `iface` | The routed interface on which the MAC bypass rule is applied. |
| `MAC`   | The MAC address that is allowed to bypass RADIUS authentication. |
| `Hits`  | The number of times this bypass rule has been matched. |

### Known Clients
This section lists clients that have been seen or authenticated via RADIUS on routed interfaces.

| Column          | Description |
|-----------------|-------------|
| `iface`         | The routed interface through which the client is connected. |
| `MAC`           | The MAC address of the client. |
| `Age(ms)`       | The duration, in milliseconds, since the client entry was created or last refreshed. |
| `Last Check(ms)`| The time, in milliseconds, since the client's authentication status was last checked. |
| `Flags`         | Flags indicating the status or attributes of the client's session (e.g., authenticated, pending). Specific flag meanings may require further VeloCloud internal documentation. |
| `Hits`          | The number of packets or connection attempts associated with this client. |