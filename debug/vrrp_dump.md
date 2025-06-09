#	--vrrp_dump

##	Description
This command displays the High Availability (HA) Virtual Router Redundancy Protocol (VRRP) state of the VeloCloud Edge. It provides information about the HA configuration, VRRP instance counts, and basic health indicators.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --vrrp_dump
{
  "ha_type": "none",
  "icmp_response_to_echo_req": 0,
  "pathUp": 0,
  "total_vrrp_active_instance": 0,
  "total_vrrp_instance": 0
}
```

##  Field descriptions
| Column | Description |
|---|---|
| `ha_type` | Indicates the High Availability mode configured on the Edge. "none" signifies that HA is not configured or active. Other potential values could relate to specific HA pairing states. |
| `icmp_response_to_echo_req` | A counter for ICMP echo responses to echo requests, often used in VRRP health monitoring to determine reachability or liveness of VRRP peers. |
| `pathUp` | A status indicator for the VRRP path. A value of `0` typically means the path is down or not established, while `1` would indicate the path is up. |
| `total_vrrp_active_instance` | The number of VRRP instances on this Edge that are currently in the "active" (or "master") state, meaning they are responsible for forwarding traffic for their respective virtual IP addresses. |
| `total_vrrp_instance` | The total number of VRRP instances configured on this Edge, regardless of their current state (active or backup). |