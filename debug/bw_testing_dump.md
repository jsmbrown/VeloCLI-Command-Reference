#	--bw_testing_dump

##	Description
This command dumps the current bandwidth test data, including current reschedule status. Bandwidth testing is a crucial component of the VeloCloud SD-WAN solution, used to assess the capacity and quality of underlying WAN links. This information is utilized by the VeloCloud Orchestrator and Edges for path selection, Quality of Experience (QoE) calculations, and Dynamic Multipath Optimization (DMPO) decisions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. But you need to run "debug --debug_bw_test {Interface}" with interface as an argument to get correct output |

##  Example usage

```
example_com:velocli> debug --debug_bw_test GE1
{
  "GE1": "Bandwidth test request is being processed"
}

example_com:velocli>
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
| bw_mode | Displays if it is mesured manually, slow start, Burst mode |
| bw_test_count| Displays bandwidth test count |
| bw_undermeasure_retry_count | Displays bandwidth undermeasure retry count |
| bw_unmeasurable_retry_count | Displays bandwidth unmeasurable retry count |
| iface_name | Displays Interface name |
| link_bw_test_in_progress | Displays link bandwidth test in progress  |
| link_name | Displays link name |
| logicalId | Displays logical Id |
| measure_time | Displays measure time |  
| path_bw_test_queued | Displays path bandwidth test queued  |
| reschedule_in_progress | Displays reschedule in progress |
| reschedule_timer | Displays reschedule timer |
| rx_bw_kbps | Displays rx bandwidth in kbps |
| rx_test_in_progress |  Displays rx test in progress |
| td_version |  Displays td version |
| tx_bw_kbps |  Displays tx bandwidth in kbps |
| tx_test_in_progress | Displays tx test in progress |
