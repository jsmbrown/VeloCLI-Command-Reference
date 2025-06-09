#	--nvs_list

##	Description
Dumps the current status of all configured Non-VeloCloud Site (NVS) paths. NVS, also referred to as Non-SD-WAN Destinations (NSD), are non-SD-WAN endpoints (like third-party security services or legacy VPN concentrators) to which VeloCloud Edges or Gateways establish IPSec or GRE tunnels. This command provides insights into the state and configuration of these connections.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --nvs_list
Name               Destination                                  Link  Protocol    State  Forwarding State  L7 State  Cookie  Source IP      Server IP            Policy  Segment
ZScalerEdgeIPsec        Backup  00000001-3913-4132-bca0-dd18bdf45da5     IPsec  STANDBY              DOWN   UNKNOWN       0        TBD  165.225.0.165  biz_policy_based        1
ZScalerEdgeIPsec       Primary  00000001-3913-4132-bca0-dd18bdf45da5     IPsec       UP        FORWARDING        UP     0x3        TBD  170.85.14.130  biz_policy_based        1
```

##  Field descriptions
| Column           | Description                                                                                                |
|------------------|------------------------------------------------------------------------------------------------------------|
| Name             | The user-defined name for the Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD) configuration.      |
| Destination      | Indicates if this specific path is designated as 'Primary' or 'Backup' for the NVS.                        |
| Link             | The internal identifier of the VeloCloud Edge's WAN link used for this NVS path.                           |
| Protocol         | The tunneling protocol used for the connection (e.g., `IPsec`, `GRE`).                                     |
| State            | The operational state of the tunnel (e.g., `UP`, `DOWN`, `STANDBY`).                                       |
| Forwarding State | The data plane forwarding state for this path (e.g., `FORWARDING`, `DOWN`).                                |
| L7 State         | The Layer 7 health check status, particularly relevant for Cloud Security Services (CSS) like ZScaler (e.g., `UP`, `DOWN`, `UNKNOWN`). |
| Cookie           | An internal identifier or session cookie, likely used for tunnel management or state tracking.             |
| Source IP        | The source IP address of the VeloCloud Edge used for this tunnel. `TBD` (To Be Determined) may indicate dynamic assignment or that the IP is not yet established. |
| Server IP        | The destination IP address of the NVS endpoint.                                                            |
| Policy           | The name of the business policy or routing policy associated with traffic directed over this NVS path.     |
| Segment          | The network segment ID to which this NVS connection is associated on the VeloCloud Edge.                   |