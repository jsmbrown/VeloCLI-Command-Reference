#	--user_firewall_flush [all | <src_ip>] [all | <dest_ip>]

##	Description
Flushes active stateful firewall sessions on the VeloCloud Edge. This command allows administrators to clear all existing user traffic firewall sessions or selectively clear sessions based on source and/or destination IP addresses. This operation is typically used for troubleshooting network connectivity issues or to ensure that new or modified firewall policies are applied immediately to traffic without waiting for existing sessions to naturally time out.

##  Arguments (optional)
The command accepts up to two optional positional arguments to filter the sessions to be flushed.

| Argument | Description |
|---|---|
| `all` \| `<src_ip>` | (Optional) The first argument, specifying the source IP address for filtering sessions. <br> - Provide a specific IP address (e.g., `192.168.1.100`) to flush only sessions originating from that source. <br> - Use the keyword `all` to match sessions from any source IP. <br> If this argument is omitted (and no second argument is provided), it defaults to `all` source IPs. |
| `all` \| `<dest_ip>` | (Optional) The second argument, specifying the destination IP address for filtering sessions. <br> - Provide a specific IP address (e.g., `8.8.8.8`) to flush only sessions destined for that IP. <br> - Use the keyword `all` to match sessions to any destination IP. <br> If this argument is omitted, it defaults to `all` destination IPs. This argument is positional and must be preceded by the first argument (e.g., `<src_ip>` or `all`). |

If no arguments are provided, all active user firewall sessions are flushed.

##  Example usage
To flush all active user firewall sessions:
```
example_com:velocli> debug --user_firewall_flush
```

To flush only sessions originating from source IP `192.168.10.50` (to any destination):
```
example_com:velocli> debug --user_firewall_flush 192.168.10.50
```

To flush only sessions destined for IP `8.8.8.8` from any source:
```
example_com:velocli> debug --user_firewall_flush all 8.8.8.8
```

To flush only sessions from source IP `192.168.10.50` to destination IP `8.8.8.8`:
```
example_com:velocli> debug --user_firewall_flush 192.168.10.50 8.8.8.8
```

##  Field descriptions
| Column | Description |
|---|---|
|   | This command does not produce tabular output. Upon successful execution, it typically returns to the command prompt. A confirmation message may be displayed, or an error message if the arguments are invalid or the operation fails. |