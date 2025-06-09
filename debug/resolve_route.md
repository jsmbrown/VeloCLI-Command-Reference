#	--resolve_route [prefix] [all|segment-id]

##	Description
This command displays the results of Recursive Next Hop (NH) Resolution for IP prefixes on a VeloCloud Edge. Recursive Next Hop Resolution is the process by which the Edge determines the ultimate path or interface for forwarding traffic to a destination, potentially involving multiple lookups through various routing tables and tunnel information within the SD-WAN overlay.

##  Arguments (optional)
The command accepts up to two positional arguments. If no arguments are provided, it displays usage information.

| Argument     | Description                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------|
| `prefix`     | The IP prefix (e.g., `192.168.1.0/24` or `2001:db8::/32`) for which to resolve the route. This is the first positional argument. |
| `all`        | A keyword used as the second positional argument. If specified, route resolution details are shown for the given `prefix` across all configured network segments. |
| `segment-id` | A numerical identifier for a specific network segment (e.g., `0`, `1`). If provided as the second positional argument, route resolution for the given `prefix` is scoped to this segment. |

##  Example usage
The following example shows the output when `debug --resolve_route` is run without any arguments, which results in the display of usage instructions:
```
example_com:velocli> debug --resolve_route
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##  Field descriptions
| Column | Description |
|---|---|
|   |  (Actual output fields for successful execution are not shown in the provided example.) |