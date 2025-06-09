#	--dynbw_config_dump

##	Description
Dump the dynamic bandwidth configuration information. This command displays the parameters that govern how the VeloCloud Edge dynamically adjusts its bandwidth utilization on network paths. These settings are crucial for optimizing performance, especially in conjunction with features like Dynamic Error Correction (DEC), by allowing the Edge to adapt to changing network conditions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --dynbw_config_dump
[
  {
    "bw_dec_min_kbps": 2000,
    "bwdecr_time": 30000,
    "bwincr_maxtime": 8,
    "bwincr_time": 4000
  }
]
```

##  Field descriptions
The output is a JSON array containing objects, where each object represents a dynamic bandwidth configuration profile. The fields within each object are described below:

| Field             | Description |
|-------------------|-------------|
| `bw_dec_min_kbps` | The minimum bandwidth threshold in Kilobits per second (Kbps) to which the system can decrease. This is often related to Dynamic Error Correction (DEC) mechanisms, ensuring a baseline bandwidth is maintained. |
| `bwdecr_time`     | The time interval in milliseconds. If network conditions suggest a need for bandwidth reduction (e.g., sustained congestion or underutilization after a peak), the system may wait for this duration before attempting to decrease bandwidth. |
| `bwincr_maxtime`  | The maximum number of incremental steps or a maximum time duration (in multiples of `bwincr_time` or a fixed unit) for which the system will attempt to increase bandwidth when conditions are favorable. This prevents runaway bandwidth increases. |
| `bwincr_time`     | The time interval in milliseconds. If network conditions are good and there is demand, the system may attempt to increase the available bandwidth after this interval. |