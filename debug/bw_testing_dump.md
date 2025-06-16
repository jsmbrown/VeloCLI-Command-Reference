#	--bw_testing_dump

##	Description
This command displays the current bandwidth test data for the VeloCloud Edge. It provides insights into the ongoing or completed bandwidth measurement processes for the WAN links, including the mode of operation, test counts, and retry attempts.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --bw_testing_dump
[
  {
    "link": {
      "bw_mode": "BURST MODE",
      "bw_test_count": 0,
      "bw_undermeasure_retry_count": 0
    }
  }
]
```
##  Field descriptions
| Field | Description |
|---|---|
| `link` | An object containing details about a specific WAN link's bandwidth testing. |
| `link.bw_mode` | Indicates the current mode of bandwidth measurement for the link. "BURST MODE" suggests the link is currently allowed to use its full available bandwidth, often after an initial measurement phase or when not actively testing. |
| `link.bw_test_count` | The number of bandwidth tests that have been performed on this link. |
| `link.bw_undermeasure_retry_count` | The number of times a bandwidth test has been retried due to the measured bandwidth being lower than expected or previous stable measurements, potentially indicating a temporary issue or inaccurate test. |