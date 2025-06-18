#	--debug_bw_test

##	Description
Run a bandwidth test on the path(s) connected through an interface.

##  Arguments
| Column | Description |
|---|---|
| Interface| add interface as an argument | 

##  Example usage
```
example_com:velocli> debug --debug_bw_test GE1
{
  "GE1": "Bandwidth test request is being processed"
}
example_com:velocli> debug --bw_testing_dump
[
  {
    "link": {
      "bw_mode": "BURST MODE",
      "bw_test_count": 0,
      "bw_undermeasure_retry_count": 0,
      "bw_unmeasurable_retry_count": 0,
      "iface_name": "GE1",
      "link_bw_test_in_progress": 1,
      "link_name": "Microsoft",
      "logicalId": "12:34:56:78:9a:bc:0000",
      "measure_time": 1750266841
    },
    "path_bw_test_queued": 0,
    "reschedule_in_progress": 0,
    "reschedule_timer": 0,
    "rx_bw_kbps": 0,
    "rx_test_in_progress": 0,
    "td_version": "1586869105",
    "tx_bw_kbps": 0,
    "tx_test_in_progress": 0
  },
  {
    "link": {
      "bw_mode": "BURST MODE",
      "bw_test_count": 0,
      "bw_undermeasure_retry_count": 0,
      "bw_unmeasurable_retry_count": 0,
      "iface_name": "GE1",
      "link_bw_test_in_progress": 1,
      "link_name": "Microsoft",
      "logicalId": "12:34:56:78:9a:bc:0000",
      "measure_time": 1750266841
    },
    "path_bw_test_queued": 0,
    "reschedule_in_progress": 0,
    "reschedule_timer": 0,
    "rx_bw_kbps": 0,
    "rx_test_in_progress": 0,
    "td_version": "1592234199",
    "tx_bw_kbps": 0,
    "tx_test_in_progress": 0
  },
  {
    "link": {
      "bw_mode": "BURST MODE",
      "bw_test_count": 0,
      "bw_undermeasure_retry_count": 0,
      "bw_unmeasurable_retry_count": 0,
      "iface_name": "GE1",
      "link_bw_test_in_progress": 1,
      "link_name": "Microsoft",
      "logicalId": "12:34:56:78:9a:bc:0000",
      "measure_time": 1750266841
    },
    "path_bw_test_queued": 0,
    "reschedule_in_progress": 0,
    "reschedule_timer": 0,
    "rx_bw_kbps": 0,
    "rx_test_in_progress": 0,
    "td_version": "1632721189",
    "tx_bw_kbps": 0,
    "tx_test_in_progress": 0
  }
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
