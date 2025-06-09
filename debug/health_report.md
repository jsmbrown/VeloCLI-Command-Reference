#	--health_report

##	Description
Dumps various health and status information about the VeloCloud Edge. This includes metrics related to system resource utilization like CPU and memory, as well as network flow counts. This information is useful for assessing the current operational state and performance of the Edge.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --health_report
{
  "active_flow_count": 148,
  "cpu_300s_avg_pct": "2.5",
  "cpu_60s_avg_pct": "1.5",
  "cpu_usage_percent": "0.0",
  "edged_mem_usage_pct": "37.6"
}
```

##  Field descriptions
| Field                 | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `active_flow_count`   | The current number of active network flows being processed by the Edge.     |
| `cpu_300s_avg_pct`    | The average CPU utilization percentage over the last 300 seconds (5 minutes). |
| `cpu_60s_avg_pct`     | The average CPU utilization percentage over the last 60 seconds (1 minute).   |
| `cpu_usage_percent`   | The instantaneous CPU utilization percentage.                               |
| `edged_mem_usage_pct` | The percentage of memory currently being used by the `edged` process, which is the main dataplane process on the VeloCloud Edge. |