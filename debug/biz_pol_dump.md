#	--biz_pol_dump [[all | segment-id] [all | policy-name]]

##	Description
This command displays the current business policies configured on the VeloCloud Edge. Business policies are a core component of the VeloCloud SD-WAN solution, allowing administrators to define how different types of application traffic are steered across the available WAN paths based on application characteristics, link quality (QoE), and business intent. This command provides insights into the policy name, segment, Conditional Backhaul (CBH) status, hit count, routing behavior, priority, traffic type, link steering preferences, and error correction settings.

##  Arguments (optional)
| Argument      | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `all`         | (Default if no arguments are provided) Displays all business policies.        |
| `segment-id`  | Filters the output to display business policies for a specific segment ID.    |
| `policy-name` | Filters the output to display a specific business policy by its name.       |

##  Example usage
```
example_com:velocli> debug --biz_pol_dump
Name                             Seg  CBH    Hits  RouteType    Prio    TrafficType   |   Routepolicy  ServiceGroup   LinkPolicy   LinkMode  Interface                             LinkLogId  ErrorCorrection
OpenDNS 208.67.222.222             0    0       0      E2Any  normal  transactional   |        direct           all   bw_balance       auto       auto  00000000-0000-0000-0000-000000000000            nack-
OpenDNS 208.67.220.220             0    0       0      E2Any  normal  transactional   |        direct           all   bw_balance       auto       auto  00000000-0000-0000-0000-000000000000            nack-
VCMP                               0    0       0      E2Any    high  transactional   |        direct           all   bw_balance       auto       auto  00000000-0000-0000-0000-000000000000            nack-
VeloCloud Management               0    1   48615      E2Any    high  transactional   |       gateway           all  loadbalance       auto       auto  00000000-0000-0000-0000-000000000000            nack-
VeloCloud SDA Client Connector     0    0       0      E2Any    high  transactional   |        direct           all        fixed  mandatory       auto  00000000-0000-0000-0000-000000000000             none
```

##  Field descriptions
| Column          | Description                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------|
| `Name`          | The name of the business policy.                                                                           |
| `Seg`           | The Segment ID to which this policy applies.                                                               |
| `CBH`           | Conditional Backhaul status for this policy. `1` indicates CBH configuration will be honored for traffic matching this policy, `0` indicates it is disabled.   |
| `Hits`          | The number of times this policy has been matched by traffic flows.                                         |
| `RouteType`     | The type of route defined by the policy (e.g., `E2Any` for Edge to Any destination)., `E2C`                       |
| `Prio`          | Priority assigned to traffic matched in the policy (`low`, `normal`, or `high`).         |
| `TrafficType`   | The classification assigned to traffic matched by this policy (`transactional`, `realtime`, or `bulk`).          |
| `Routepolicy`   | The routing action for the traffic (e.g., `direct` for local internet breakout, `gateway` for backhauling via a VeloCloud Gateway. |
| `ServiceGroup`  | The service group associated with the policy (e.g., `all`, or a specific Cloud Security Service (CSS)).    |
| `LinkPolicy`    | The link steering strategy (e.g., `bw_balance` for direct route policy with link mode auto, `loadbalance` for gateway route policy with link mode auto, `replicate` for non-fixed realtime high or normal, `fixed` for a mandatory/preferred traffic steering). |
| `LinkMode`      | The mode for link selection (e.g., `auto`, or `mandatory`/`preferred` to enforce a specific link or path type).           |
| `Interface`     | The specific WAN interface selected if `LinkMode` is set to use a particular interface, otherwise `auto`.  |
| `LinkLogId`     | Logical ID of the link or path, or all zeros if not steering traffic to a specific link/interface.                              |
| `ErrorCorrection`| The Dynamic Error Correction (DEC) setting applied (e.g., `nack-` TCP traffic, `replicate` for realtime high/normal, or `none`).             |