# --pkt_tracker [any|sip] [any|sport] [any|dip] [any|dport] [any|proto] [count of packets]

## Description
Track the life cycle of a flow. This command allows users to specify filters for source/destination IP addresses and ports, protocol, and the number of packets to track, enabling detailed observation of specific network traffic as it traverses the VeloCloud Edge.

## Arguments (optional)
The arguments are positional and optional. If no arguments are provided, the command typically displays help text or defaults to tracking all flows with a default packet count.

| Argument             | Description                                                                                                                                                              |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `[any|sip]`          | First positional argument. Specifies the source IP address to filter on (e.g., `192.168.1.10`) or the literal keyword `any` to match any source IP. If all arguments are omitted, filters default to `any`. |
| `[any|sport]`        | Second positional argument. Specifies the source port to filter on (e.g., `12345`) or the literal keyword `any` to match any source port. Defaults to `any` if not provided. |
| `[any|dip]`          | Third positional argument. Specifies the destination IP address to filter on (e.g., `8.8.8.8`) or the literal keyword `any` to match any destination IP. Defaults to `any` if not provided. |
| `[any|dport]`        | Fourth positional argument. Specifies the destination port to filter on (e.g., `443`) or the literal keyword `any` to match any destination port. Defaults to `any` if not provided. |
| `[any|proto]`        | Fifth positional argument. Specifies the protocol to filter on (e.g., `tcp`, `udp`, `icmp`) or the literal keyword `any` to match any protocol. Defaults to `any` if not provided. |
| `[count of packets]` | Sixth positional argument. Specifies the number of packets to capture and track for the identified flow. If omitted, a default system behavior (e.g., a default count or continuous tracking) will apply. |

## Example usage
```
example_com:velocli> debug --pkt_tracker
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

## Field descriptions
| Column | Description |
|---|---|
| N/A    | The example usage provided shows the help text that is displayed when the command is run without specific filter arguments. The actual output of a successful packet tracking operation, which would detail the lifecycle of packets for the specified flow (e.g., packet headers, path selection, QoE metrics, DEC actions), is not shown in this example. Therefore, field descriptions for the packet tracking output cannot be provided here. |