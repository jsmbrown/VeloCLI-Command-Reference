#	--handoffqdbg [<nothing>|<reset>]

##	Description
This command is used to display information related to handoff queues or to reset their counters. Handoff queues are internal queues used by the VeloCloud Edge to pass packets between different processing threads or modules, such as between network interface input and IPsec processing. Monitoring these queues can help diagnose performance issues or packet drops within the Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<nothing>` | If no argument is provided, the command dumps the current statistics for all handoff queues. |
| `reset` | If `reset` is specified, the command resets the counters for all handoff queues. |

##  Example usage
```
example_com:velocli> debug --handoffqdbg
name                        tid  qlimit    enq    deq  drops  qlength  wmark  wmark_1min  wmark_5min
netif_queue0                  0       0    371    371      0        0      1           0           0
per_core_queue0               0   16384  24701  24701      0        0      3           0           0
ipsec_exception_q             0       0      1      1      0        0      0           0           0
gre_exception_q               0       0      0      0      0        0      0           0           0
vc_queue_link_cos         15784    4096      0      0      0        0      0           0           0
```

##  Field descriptions
| Column | Description |
|---|---|
| `name` | The name of the specific handoff queue. |
| `tid` | Thread ID associated with this queue. A value of 0 often indicates it's not tied to a specific worker thread or is a global queue. |
| `qlimit` | The configured maximum limit (depth) of the queue in terms of the number of packets it can hold. A value of 0 might indicate an effectively unlimited or dynamically sized queue. |
| `enq` | The total number of packets enqueued into this queue since the last counter reset or system start. |
| `deq` | The total number of packets dequeued (processed) from this queue since the last counter reset or system start. |
| `drops` | The total number of packets dropped from this queue, typically because the queue was full when a new packet arrived. |
| `qlength` | The current number of packets in the queue at the time the command was run. |
| `wmark` | The high watermark, representing the maximum queue length observed since the last counter reset or system start. |
| `wmark_1min` | The high watermark for queue length observed in the last 1 minute. |
| `wmark_5min` | The high watermark for queue length observed in the last 5 minutes. |