#	--limit_ctrl_traffic_frequency [clock_sync_interval_min=<min> disable_hb_probe=<1 or 0> traffic_hb_ms=<ms>]

##	Description
Displays the current status and configuration parameters for the Limit Control Traffic Frequency feature (added in release 6.4). This feature helps reduce the amount of control communication between the VeloCloud Edge and the VeloCloud Orchestrator or Gateways on wireless links, which can be beneficial in environments with constrained or metered WAN links. The command shows whether the feature is enabled, the interval for clock synchronization packets, if heartbeat probes are disabled, and the heartbeat interval when traffic limiting is active.

##  Arguments
| Argument | Description |
|---|---|
| none | Displays the current control traffic frequency settings |
| clock_sync_interval_min=<min> disable_hb_probe=<1 or 0> traffic_hb_ms=<ms> | Sets the control traffic frequency settings to the values specified.  i.e., to set the clock sync interval to 60 minutes, disable the heartbeat probes, and set the traffic heartbeat interval to 300ms use `clock_sync_interval_min=60 disable_hb_probe=1 traffic_hb_ms=300` |

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
| `disable_hb_probe_limit_ctrl_pkt`   | Indicates whether heartbeat probes are disabled (`true`) or enabled (`false`) on wireless links when control traffic limiting is active. Disabling probes reduces control traffic but may impact the speed of path down detection. |
| `limit_ctrl_traffic_enabled`        | Shows the status of the control traffic limiting feature. `0` indicates disabled, while `1` indicates enabled. |
| `traffic_hb_ms_limit_ctrl_pkt`      | The interval, in milliseconds (ms), for sending heartbeat (HB) packets when control traffic limiting is active. A higher value means less frequent heartbeats. |