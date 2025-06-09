#	--bwcap

##	Description
Displays information about the link bandwidth capabilities and the dynamic bandwidth testing process on the VeloCloud Edge. This command provides insights into how the Edge determines and adjusts the available bandwidth on its WAN links.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --bwcap
VCEID   CurCap  OrigCap   wstart     decr     incr     test    force  Nforced  pkts  nacks  rxkbps  txkbps  abort  init  netcap  delta  minlat  avglat
             0        0  3684803  3684803  3684803  3684803  3684803        0     0      0       0       0      1     0       0      0       0       0
```

##  Field descriptions
| Column  | Description                                                                 |
|---------|-----------------------------------------------------------------------------|
| VCEID   | VeloCloud Edge Identifier.                                                  |
| CurCap  | Current measured bandwidth capacity of the link in Kbps.                      |
| OrigCap | Original or initial bandwidth capacity of the link in Kbps.                 |
| wstart  | Internal value related to the start of a bandwidth measurement window.      |
| decr    | Internal value related to bandwidth decrement calculations.                 |
| incr    | Internal value related to bandwidth increment calculations.                 |
| test    | Internal value related to the bandwidth test being performed.               |
| force   | Indicates if a bandwidth capacity has been manually forced or overridden.   |
| Nforced | Number of times the bandwidth capacity has been forced.                     |
| pkts    | Number of packets involved in the bandwidth measurement.                    |
| nacks   | Number of negative acknowledgements received during bandwidth testing.      |
| rxkbps  | Measured receive bandwidth in Kilobits per second.                          |
| txkbps  | Measured transmit bandwidth in Kilobits per second.                         |
| abort   | Number of times the bandwidth test was aborted.                             |
| init    | Indicates the initialization state or count of the bandwidth test.          |
| netcap  | Network capacity, potentially an aggregated or overall capacity figure.     |
| delta   | The difference or change observed in bandwidth measurements.                |
| minlat  | Minimum latency observed during the bandwidth test period in milliseconds.  |
| avglat  | Average latency observed during the bandwidth test period in milliseconds.  |