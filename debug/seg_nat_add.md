#	--seg_nat_add app-name <seg-id> <dest-ip> <dport> <protocol> <iface_name>

##	Description
Add a static entry to the segment Network Address Translation (NAT) table. This allows for specific mapping of traffic based on application, segment, destination IP, port, protocol, and interface.

##  Arguments (mandatory)
| Argument | Description |
|---|---|
| `app-name` | A user-defined name for the application or rule. |
| `<seg-id>` | The ID of the VeloCloud SD-WAN segment to which this NAT rule applies. |
| `<dest-ip>` | The destination IP address for the NAT entry. |
| `<dport>` | The destination port for the NAT entry. |
| `<protocol>` | The network protocol for the NAT entry (e.g., TCP, UDP, ICMP). |
| `<iface_name>` | The name of the network interface (e.g., GE1, LAN1) associated with this NAT rule. |

##  Example usage
The following example shows the output when the command is run without the required arguments, displaying the general usage help for the `debug.py` script.
```
example_com:velocli> debug --seg_nat_add
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A successful command execution would require all mandatory arguments to be provided, for example:
`example_com:velocli> debug --seg_nat_add MyApp 1 192.168.10.5 443 TCP GE1`
(Note: The output of a successful command is not shown in the provided example.)

##  Field descriptions
| Column | Description |
|---|---|
|   |  (No output fields are detailed as the example usage shows a help message.) |