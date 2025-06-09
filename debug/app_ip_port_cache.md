#	--app_ip_port_cache [v4 | v6 | all]

##	Description
Displays the current cache of "fast learned" IP routable applications. This cache is populated by the VeloCloud Edge as it observes traffic, allowing for quicker identification and policy application for subsequent flows matching these IP addresses and ports. This is particularly useful for applications that are not initially identified by Deep Packet Inspection (DPI) but are learned through traffic patterns or application mapping.

##  Arguments (optional)
| Argument | Description |
|---|---|
| v4 | Displays only IPv4 entries in the application IP port cache. |
| v6 | Displays only IPv6 entries in the application IP port cache. |
| all | Displays all entries (both IPv4 and IPv6) in the application IP port cache. This is the default behavior if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --app_ip_port_cache
IP ADDR      PORT  APPLICATION                        CLASS  DPI/AppMap  IDLE TIME MS  IS DEFAULT  IS FQDN
172.30.0.6     22      APP_SSH  APP_CLASS_TUNNELING_AND_VPN         APM          1821           0        0

example_com:velocli> debug --app_ip_port_cache v4
IP ADDR      PORT  APPLICATION                        CLASS  DPI/AppMap  IDLE TIME MS  IS DEFAULT  IS FQDN
172.30.0.6     22      APP_SSH  APP_CLASS_TUNNELING_AND_VPN         APM          1821           0        0
```

##  Field descriptions
| Column | Description |
|---|---|
| IP ADDR | The IP address associated with the learned application. |
| PORT | The port number associated with the learned application. |
| APPLICATION | The name of the application identified for this IP address and port combination (e.g., APP_SSH). |
| CLASS | The classification category of the application (e.g., APP_CLASS_TUNNELING_AND_VPN). |
| DPI/AppMap | Indicates the method of application identification. 'APM' likely refers to Application Mapping, while 'DPI' would indicate Deep Packet Inspection. |
| IDLE TIME MS | The duration in milliseconds for which this cache entry has been idle (i.e., no matching traffic observed). |
| IS DEFAULT | A flag (0 or 1) indicating whether this is a default or system-defined entry. '0' typically means it was dynamically learned. |
| IS FQDN | A flag (0 or 1) indicating whether the application identification was based on a Fully Qualified Domain Name (FQDN). '0' typically means it was not. |