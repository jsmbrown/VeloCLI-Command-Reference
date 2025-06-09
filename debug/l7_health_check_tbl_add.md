#	--l7_health_check_tbl_add &lt;seg-id&gt; &lt;dest-ip&gt; &lt;nvs-logical-id&gt; &lt;link-logical-id&gt; &lt;nvs-ip&gt; &lt;dst-port&gt;

##	Description
This command inserts a new entry into the Layer 7 (L7) health check hash table on the VeloCloud Edge. L7 health checks are used to monitor the status and performance of specific applications or services, often those hosted on Non-VeloCloud Sites (NVS) or other critical destinations. The information gathered from these health checks can influence routing decisions and application availability.

##	Arguments (Mandatory)
These arguments must be provided in the specified order.

| Argument          | Description                                                                                                                               |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `<seg-id>`        | The segment ID to which this Layer 7 health check entry applies. VeloCloud Edges support network segmentation for multi-tenancy or traffic isolation. |
| `<dest-ip>`       | The destination IP address of the service or application endpoint that is being monitored by this Layer 7 health check.                     |
| `<nvs-logical-id>`| The logical identifier (often a UUID) of the Non-VeloCloud Site (NVS) associated with this health check. This is relevant if the health check targets a service reached via an NVS. |
| `<link-logical-id>`| The logical identifier (often a UUID or specific interface ID) of the WAN link on the Edge over which this health check probe is performed. |
| `<nvs-ip>`        | The IP address of the Non-VeloCloud Site (NVS) endpoint or gateway that is relevant to this health check path.                            |
| `<dst-port>`      | The destination port number used for the Layer 7 health check probe (e.g., 80 for HTTP, 443 for HTTPS, or a custom application port).      |

##	Example Usage
This example demonstrates adding an L7 health check entry for a service at IP `198.51.100.25` on port `443`, associated with segment `1`, a specific NVS, and a specific link.
```
example_com:velocli> debug --l7_health_check_tbl_add 1 198.51.100.25 a1b2c3d4-e5f6-7890-1234-567890abcdef lnk-uuid-ge2-wan0 203.0.113.50 443
L7 health check entry added successfully.
```
**Note:** If the command is entered without the required arguments, a usage message similar to the following will be displayed:
```
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ...
```

##	Field Descriptions
This command is used to add an entry to the Layer 7 health check hash table. Upon successful execution, it typically returns a confirmation message indicating the success or failure of the operation, as shown in the example above. It does not produce a tabular output of data fields itself.

To view the contents of the L7 health check table, a different command (e.g., a command designed to dump or show the table) would be used.