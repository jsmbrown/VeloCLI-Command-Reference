# --enable_netflow &lt;Collector&gt; &lt;port&gt; &lt;source_interface&gt;

## Description
Enables the Netflow exporter on the VeloCloud Edge, allowing it to send Netflow data to a specified collector. Netflow provides visibility into network traffic patterns and volume.

## Arguments (required)
| Argument           | Description                                                                                                |
|--------------------|------------------------------------------------------------------------------------------------------------|
| `<Collector>`      | The IP address or hostname of the Netflow collector device or server that will receive the Netflow data.     |
| `<port>`           | The UDP port number on which the Netflow collector is listening. Common Netflow ports include 2055, 9995, or 9996. |
| `<source_interface>` | The name of the network interface on the VeloCloud Edge (e.g., GE1, LAN1) that will be used as the source of the exported Netflow packets. |

## Example usage
The following example shows the output when `debug --enable_netflow` is executed without the required arguments. This typically results in the system displaying usage instructions for the command.
```
example_com:velocli> debug --enable_netflow
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```