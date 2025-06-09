#	`--packet_pair_debug <tx|rx> <peer_logical_id>`

##	Description
Dump the packet pair debug info for tx and rx. This command is used to retrieve diagnostic information related to the packet pair mechanism, which is often employed for measuring network path characteristics like bandwidth to a peer.

##  Arguments
These are mandatory positional arguments that must follow the command.

| Argument            | Description                                                                                                |
|---------------------|------------------------------------------------------------------------------------------------------------|
| `<tx|rx>`            | Specifies the direction of traffic for the packet pair debug information. Use `tx` for transmit or `rx` for receive. |
| `<peer_logical_id>` | The logical identifier of the peer VeloCloud Edge or Gateway for which packet pair debug information is requested. |

##  Example usage
The following example demonstrates the output when `debug --packet_pair_debug` is issued without the required arguments. In this scenario, the system displays a general usage message for the `debug.py` script, as the specific arguments for `--packet_pair_debug` were not provided.

```
example_com:velocli> debug --packet_pair_debug
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A correct invocation would look like: `debug --packet_pair_debug tx 01234567-89ab-cdef-0123-456789abcdef` (with a valid peer logical ID).

##  Field descriptions
The example output shown above is a help message because the command was invoked without its mandatory arguments. Therefore, specific output fields for the `--packet_pair_debug` command (when correctly used) are not illustrated in this example. When executed with valid `tx|rx` and `peer_logical_id` arguments, the command would display detailed debug information pertaining to packet pair operations for the specified peer and direction.