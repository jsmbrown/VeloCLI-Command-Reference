#	--app_proto_port_db

##	Description
This command displays the VeloCloud Edge's current database of applications that are identifiable by their transport protocol (TCP or UDP) and port number. This list is used by the Edge to classify network traffic for Quality of Service (QoS) and routing decisions.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --app_proto_port_db
PORT    PROTOCOL         APPLICATION                             CLASS
7            TCP            APP_ECHO              APP_CLASS_MANAGEMENT
7            UDP            APP_ECHO              APP_CLASS_MANAGEMENT
20           TCP        APP_FTP_DATA            APP_CLASS_FILE_SHARING
21           TCP             APP_FTP            APP_CLASS_FILE_SHARING
22           TCP             APP_SSH       APP_CLASS_TUNNELING_AND_VPN
```

##  Field descriptions
| Column      | Description                                      |
|-------------|--------------------------------------------------|
| PORT        | The network port number used by the application. |
| PROTOCOL    | The transport layer protocol (e.g., TCP, UDP).   |
| APPLICATION | The internal name used by the VeloCloud system to identify the application. |
| CLASS       | The category or class the application belongs to, often used for policy enforcement or QoE. |