#	`--rss_hash_calc ('<src_ip>', '<src_port>', '<dst_ip>', '<dst_port>', '<protocol>')`

##	Description
Calculate the RSS hash for a src/dst pair. This hash is used for Receive Side Scaling (RSS), a network driver technology that distributes network receive processing across multiple CPU cores on the VeloCloud Edge. This command helps in predicting or verifying how specific network flows are distributed, which can be useful for performance analysis and troubleshooting.

##	Arguments
This command requires the following five arguments to be provided in order:

| Argument     | Description                                                                                   |
|--------------|-----------------------------------------------------------------------------------------------|
| `<src_ip>`   | The source IP address of the network flow (e.g., `192.168.1.10`).                             |
| `<src_port>` | The source port number of the network flow (e.g., `12345`).                                   |
| `<dst_ip>`   | The destination IP address of the network flow (e.g., `8.8.8.8`).                             |
| `<dst_port>` | The destination port number of the network flow (e.g., `53`).                                 |
| `<protocol>` | The protocol of the network flow. This can be a name (e.g., `tcp`, `udp`) or its IP protocol number (e.g., `6` for TCP, `17` for UDP). |

##	Example usage
The following example shows the help text that is displayed if the command is run without its required arguments:
```
example_com:velocli> debug --rss_hash_calc
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A correct invocation to calculate an RSS hash would look like:
`example_com:velocli> debug --rss_hash_calc 192.168.1.100 54321 8.8.8.8 53 17`

*(The actual output for a correct invocation would be the calculated hash value, e.g., `0x1234ABCD`)*

##	Field descriptions
When executed with the correct arguments, this command outputs a single hexadecimal value representing the calculated RSS hash for the specified flow parameters. There are no specific fields or columns in the output, only the hash value itself.

The example usage provided above shows the general help text for the `debug.py` script because `--rss_hash_calc` was called without its mandatory arguments.