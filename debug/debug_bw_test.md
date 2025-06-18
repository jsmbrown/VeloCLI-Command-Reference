#	--debug_bw_test

##	Description
Run a bandwidth test on the path(s) connected through an interface.

##  Arguments
This command does not take any arguments.

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
