#	--bw_testing_dump

##	Description
This command dumps the current bandwidth test data, including current reschedule status. Bandwidth testing is a crucial component of the VeloCloud SD-WAN solution, used to assess the capacity and quality of underlying WAN links. This information is utilized by the VeloCloud Orchestrator and Edges for path selection, Quality of Experience (QoE) calculations, and Dynamic Multipath Optimization (DMPO) decisions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --debug_bw_test
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
```
example_com:velocli> debug --bw_testing_dump
[
{
   "link": {
      "bw_mode": "BURST MODE",
      "bw_test_count": 0,
      "bw_undermeasure_retry_count": 0,
      "bw_unmeasurable_retry_count": 0,
      "iface_name": "GE1",
      "link_bw_test_in_progress": 0,
      "link_name": "Microsoft",
      "logicalId": "12:34:56:78:9a:bc:0000",
      "measure_time": 1749832802
    },
    "path_bw_test_queued": 0,
    "reschedule_in_progress": 0,
    "reschedule_timer": 0,
    "rx_bw_kbps": 2371900,
    "rx_test_in_progress": 0,
    "td_version": "3629538363",
    "tx_bw_kbps": 3086228,
    "tx_test_in_progress": 0
},
]
```
##  Field descriptions
| Column | Description |
|---|---|
| bw_mode | Shows if it is mesured manually, slow start, Burst mode |
| bw_test_count| bandwidth test count |
| bw_undermeasure_retry_count | bandwidth undermeasure retry count |
| bw_unmeasurable_retry_count | bandwidth unmeasurable retry count |
| iface_name | Interface name |
| link_bw_test_in_progress | link bandwidth test in progress  |
| link_name | link name |
| logicalId | logical Id |
| measure_time | measure time |  
| path_bw_test_queued | path bandwidth test queued  |
| reschedule_in_progress | reschedule in progress |
| reschedule_timer | reschedule timer |
| rx_bw_kbps | 2371900 |
| rx_test_in_progress | 0 |
| td_version | 3629538363 |
| tx_bw_kbps | 3086228 |
| tx_test_in_progress | 0 |
