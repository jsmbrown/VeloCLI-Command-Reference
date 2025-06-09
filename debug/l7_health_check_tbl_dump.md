#	--l7_health_check_tbl_dump

##	Description
Dumps entries from the Layer 7 (L7) health check hash table. This table contains information about health checks performed for applications or services, often related to Non-VeloCloud Sites (NVS) or other destinations requiring application-level health verification.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --l7_health_check_tbl_dump
[
  {
    "dst_ip": "170.85.14.130",
    "dst_port": 7000,
    "enterprise_logical_id": "00000001-3913-4132-bca0-dd18bdf45da5",
    "nvs_ip": "165.225.216.34",
  }
]
```

##  Field descriptions
| Field                   | Description |
|-------------------------|-------------|
| `dst_ip`                | The destination IP address that is the target of the Layer 7 health check. |
| `dst_port`              | The destination port number used for the Layer 7 health check. |
| `enterprise_logical_id` | A unique logical identifier for the enterprise associated with this health check entry. |
| `nvs_ip`                | The IP address of the Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD) for which this health check is relevant. This indicates the health check is likely for a service hosted at or via this NVS. |