#	--limit_ctrl_traffic_frequency

##	Description
Displays the current status and configuration parameters for limiting control plane traffic. This feature helps reduce the amount of control communication between the VeloCloud Edge and the VeloCloud Orchestrator or Gateways, which can be beneficial in environments with constrained or metered WAN links. The command shows whether the feature is enabled, the interval for clock synchronization packets, if heartbeat probes are disabled, and the heartbeat interval when traffic limiting is active.

##  Arguments
None.

##  Example usage
```
example_com:velocli> debug --limit_ctrl_traffic_frequency
{
  "clock_sync_minutes_limit_ctrl_pkt": 30,
  "disable_hb_probe_limit_ctrl_pkt": true,
  "limit_ctrl_traffic_enabled": 0,
  "traffic_hb_ms_limit_ctrl_pkt": 500
}
```

##  Field descriptions
| Field                               | Description                                                                                                                               |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `clock_sync_minutes_limit_ctrl_pkt` | The interval, in minutes, for sending clock synchronization packets when control traffic limiting is active.                                |
| `disable_hb_probe_limit_ctrl_pkt`   | Indicates whether heartbeat (HB) probes are disabled (`true`) or enabled (`false`) when control traffic limiting is active. Disabling probes reduces control traffic but may impact the speed of path down detection. |
| `limit_ctrl_traffic_enabled`        | Shows the status of the control traffic limiting feature. `0` typically indicates disabled, while `1` (or other non-zero) indicates enabled. |
| `traffic_hb_ms_limit_ctrl_pkt`      | The interval, in milliseconds (ms), for sending heartbeat (HB) packets when control traffic limiting is active. A higher value means less frequent heartbeats. |