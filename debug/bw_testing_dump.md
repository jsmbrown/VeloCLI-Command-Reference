#	--bw_testing_dump

##	Description
This command dumps the current bandwidth test data. Bandwidth testing is a crucial component of the VeloCloud SD-WAN solution, used to assess the capacity and quality of underlying WAN links. This information is utilized by the VeloCloud Orchestrator and Edges for path selection, Quality of Experience (QoE) calculations, and Dynamic Multipath Optimization (DMPO) decisions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --bw_testing_dump
[]

example_com:velocli> "link": {
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
```
##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example output `[]` indicates that there is currently no bandwidth test data to display or that the data structure is empty. When data is present, it would typically include details about ongoing or completed bandwidth tests on various paths. |
