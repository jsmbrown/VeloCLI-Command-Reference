#	--current_apps

##	Description
Displays a list of currently identified application flows traversing the VeloCloud Edge. This includes details about the source and destination IP addresses, ports, protocol, segment, identified application, hostname (if resolved), application class, and the path taken by the flow. This command is useful for real-time monitoring of application traffic and verifying application identification and policy enforcement.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --current_apps
SRC IP                 DST IP  DST PORT  PROTOCOL  SEGID               APPLICATION       HOSTNAME                        APP CLASS                          PATH
172.30.0.6      216.221.27.88      5012         6      0              APP_SSH(198)                 APP_CLASS_TUNNELING_AND_VPN(18)              Edge2CloudDirect
172.30.1.200    172.30.255.37     61869         6      1  APP_VELOCLOUD_MGMT(4095)                         APP_CLASS_VELOCLOUD(20)                        Routed
172.30.1.200    172.30.255.37     61751         6      1  APP_VELOCLOUD_MGMT(4095)                         APP_CLASS_VELOCLOUD(20)                        Routed
172.30.1.200    172.30.255.37     61474         6      1  APP_VELOCLOUD_MGMT(4095)                         APP_CLASS_VELOCLOUD(20)                        Routed
172.30.1.200    172.30.255.37     61525         6      1  APP_VELOCLOUD_MGMT(4095)                         APP_CLASS_VELOCLOUD(20)                        Routed
```

##  Field descriptions
| Column      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| SRC IP      | Source IP address of the traffic flow.                                      |
| DST IP      | Destination IP address of the traffic flow.                                 |
| DST PORT    | Destination port number used by the traffic flow.                           |
| PROTOCOL    | IP protocol number (e.g., 6 for TCP, 17 for UDP).                           |
| SEGID       | Segment ID to which the traffic flow belongs.                               |
| APPLICATION | Name of the identified application and its internal application ID.           |
| HOSTNAME    | Hostname associated with the destination IP, if resolved.                   |
| APP CLASS   | Classification category of the application and its internal class ID.       |
| PATH        | The routing path taken by the application flow (e.g., Edge2CloudDirect, Routed, VeloCloud Path). |