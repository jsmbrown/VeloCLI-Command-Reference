#	--ike_resource

##	Description
Dumps the current Internet Key Exchange (IKE) resource statistics. This command provides insights into the IKE tables used for establishing and managing IPSec tunnels, which are fundamental for secure communication in the SD-WAN overlay, including connections to Non-VeloCloud Sites (NVS/NSD).

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --ike_resource

Table Counts
==================================================
vc_tbl_inst_id_tbl_cnt             1
vc_tbl_dynamic_tbl_cnt             1
vc_tbl_static_tbl_cnt              0
```

##  Field descriptions
| Column | Description |
|---|---|
| `vc_tbl_inst_id_tbl_cnt` | The count of entries in the VeloCloud IKE instance ID table. This table likely tracks active IKE instances. |
| `vc_tbl_dynamic_tbl_cnt` | The count of entries in the VeloCloud IKE dynamic table. This typically represents IKE Security Associations (SAs) that have been dynamically established, for example, during DE2E tunnel formation or with dynamic peer configurations. |
| `vc_tbl_static_tbl_cnt` | The count of entries in the VeloCloud IKE static table. This usually represents IKE SAs related to statically configured peers, such as those for NVS/NSD connections or statically defined hub tunnels. |