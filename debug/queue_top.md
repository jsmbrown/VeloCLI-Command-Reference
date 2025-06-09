#	--queue_top [<sort_column>]

##	Description
Provides a real-time, typically auto-refreshing, display of traffic queue statistics on the VeloCloud Edge. This command is essential for monitoring queue performance, including metrics like packet enqueues, dequeues, drops, current depth, and throughput. These statistics are often tied to Quality of Service (QoS) configurations and Business Policies, helping diagnose network congestion and policy effectiveness.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `<sort_column>` | Specifies the column name from the output table to use for sorting the queue statistics. If this argument is not provided, the output will be sorted by a default column (e.g., queue identifier or a primary activity metric like packet drops or queue depth). |

##  Example usage
```
example_com:velocli> debug --queue_top
```
The command will then display a table of queue statistics, which typically updates periodically to reflect real-time changes.

##  Field descriptions
The output table for `debug --queue_top` generally includes fields related to queue activity and performance. The exact column names and the specific metrics displayed may vary. Common fields include:

| Column | Description |
|---|---|
| `Queue ID` / `Name` | Identifier or name of the specific queue. |
| `Interface` | The network interface (e.g., GE1, GE2, USB1) associated with this queue. |
| `Policy` / `Class` | The Business Policy or traffic class that directs traffic to this queue. |
| `Pkts Enqueued` / `Pkts In` | Total number of packets that have entered this queue. |
| `Bytes Enqueued` / `Bytes In` | Total number of bytes that have entered this queue. |
| `Pkts Dequeued` / `Pkts Out` | Total number of packets that have been successfully transmitted from this queue. |
| `Bytes Dequeued` / `Bytes Out` | Total number of bytes that have been successfully transmitted from this queue. |
| `Pkts Dropped` / `Drops` | Total number of packets dropped from this queue, usually due to buffer overflow (congestion). |
| `Bytes Dropped` | Total number of bytes dropped from this queue. |
| `Current Depth (Pkts)` | The current number of packets waiting in the queue. |
| `Current Depth (Bytes)` | The current size in bytes of the data waiting in the queue. |
| `Max Depth (Pkts)` | The maximum number of packets the queue is configured to hold. |
| `Max Depth (Bytes)` | The maximum size in bytes the queue is configured to hold. |
| `Rate (pps)` | The current rate at which packets are being processed (enqueued or dequeued) by the queue, in packets per second. |
| `Rate (bps)` | The current rate at which data is being processed (enqueued or dequeued) by the queue, in bits per second. |
| `Tail Drops` | Number of packets dropped because the queue was full (tail drop). |
| `RED Drops` | Number of packets dropped by Random Early Detection (RED) or Weighted RED (WRED) mechanisms, if configured. |