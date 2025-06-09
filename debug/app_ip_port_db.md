#	--app_ip_port_db

##	Description
This command dumps the current list of fast-learned IP routable applications. The VeloCloud Edge maintains a database of applications it has identified based on IP address and port combinations. This "fast learning" allows the Edge to quickly classify traffic and apply appropriate policies for Quality of Experience (QoE) and routing.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --app_ip_port_db
IP ADDR                                                         NETMASK                                                                                 TCP_PORT(S)                                                                                                                             UDP_PORT(S)                APPLICATION                             CLASS
2620:1ec:4::152                 ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff                                                           [25, 80, 143, 443, 587, 993, 995]                                                                                                                                      []              APP_OFFICE365  APP_CLASS_BUSINESS_COLLABORATION
2620:1ec:4::153                 ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff                                                           [25, 80, 143, 443, 587, 993, 995]                                                                                                                                      []              APP_OFFICE365  APP_CLASS_BUSINESS_COLLABORATION
2620:1ec:4::192                 ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff                                                           [25, 80, 143, 443, 587, 993, 995]                                                                                                                                      []              APP_OFFICE365  APP_CLASS_BUSINESS_COLLABORATION
2620:1ec:c::10                  ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff                                                           [25, 80, 143, 443, 587, 993, 995]                                                                                                                                      []              APP_OFFICE365  APP_CLASS_BUSINESS_COLLABORATION
2620:1ec:c::11                  ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff                                                           [25, 80, 143, 443, 587, 993, 995]                                                                                                                                      []              APP_OFFICE365  APP_CLASS_BUSINESS_COLLABORATION
```

##  Field descriptions
| Column        | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| IP ADDR       | The IP address (IPv4 or IPv6) associated with the learned application.      |
| NETMASK       | The netmask corresponding to the IP address.                                |
| TCP_PORT(S)   | A list of TCP ports used by this application entry.                         |
| UDP_PORT(S)   | A list of UDP ports used by this application entry.                         |
| APPLICATION   | The internal name or identifier for the recognized application (e.g., APP_OFFICE365). |
| CLASS         | The classification category of the application (e.g., APP_CLASS_BUSINESS_COLLABORATION). This helps in applying group-based policies. |