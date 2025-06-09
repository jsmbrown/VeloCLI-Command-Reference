#	--atp_profile_dump

##	Description
Displays statistics related to Advanced Threat Prevention (ATP) packet processing. This includes the maximum, minimum, and average processing time for packets, the processing time of the last packet, and the total number of packets processed, categorized by protocol (TCP, UDP, ICMP, GRE). The command also indicates whether ATP profiling is currently enabled or disabled.

ATP is a feature that inspects traffic for security threats. Profiling helps in understanding the performance impact of this inspection.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --atp_profile_dump
ATP Profiling is Disabled
         max_time  min_time  avg_time  last_pkt  num_of_packets
TCP           0.0       0.0       0.0       0.0               0
UDP           0.0       0.0       0.0       0.0               0
ICMP          0.0       0.0       0.0       0.0               0
GRE           0.0       0.0       0.0       0.0               0
```
##  Field descriptions
| Column/Row | Description |
|---|---|
| ATP Profiling is Disabled/Enabled | Indicates the current status of ATP profiling. |
| **Protocol Rows (TCP, UDP, ICMP, GRE)** | Statistics are provided per protocol. |
| `max_time` | The maximum time (in unspecified units, likely milliseconds or microseconds) taken to process a packet of this protocol type by the ATP engine. |
| `min_time` | The minimum time (in unspecified units) taken to process a packet of this protocol type by the ATP engine. |
| `avg_time` | The average time (in unspecified units) taken to process packets of this protocol type by the ATP engine. |
| `last_pkt` | The processing time (in unspecified units) for the most recent packet of this protocol type handled by the ATP engine. |
| `num_of_packets` | The total number of packets of this protocol type processed by the ATP engine since statistics were last reset or the service started. |