#	--nat_port_dump

##	Description
Displays the VeloCloud Edge's current Network Address Translation (NAT) port table. This table shows active outbound NAT sessions, detailing the original source IP, destination IP/port, protocol, and statistics about the dynamic port allocation used for the translation. This command is useful for troubleshooting connectivity issues related to NAT port exhaustion or verifying specific NAT translations.

The command's behavior can be modified by optional positional arguments as described in the "Usage" string: `[v4 | v6 | all] [Filter list: proto|sip|dip|dport]`.

##  Arguments (optional)
The command can be followed by optional positional arguments to filter the output. Arguments must be provided in the order listed.

| Argument Position | Value | Description |
|---|---|---|
| 1st | `v4` \| `v6` \| `all` | (Optional) Filters the NAT table output by IP version. <br> - `v4`: Show only IPv4 NAT entries. <br> - `v6`: Show only IPv6 NAT entries. <br> - `all`: Show both IPv4 and IPv6 NAT entries. <br> If this argument is omitted, the command defaults to showing all entries, but subsequent filter arguments (2nd and 3rd) cannot be used. To use filters by `proto`, `sip`, `dip`, or `dport`, an IP version (e.g., `all`) must be specified in this position. |
| 2nd | `proto` \| `sip` \| `dip` \| `dport` | (Optional, requires 1st argument to be present) Specifies the type of filter to apply to the NAT table entries. This argument must be followed by a `<filter_value>` as the 3rd argument. <br> - `proto`: Filter by IP protocol number. <br> - `sip`: Filter by source IP address. <br> - `dip`: Filter by destination IP address. <br> - `dport`: Filter by destination port. |
| 3rd | `<filter_value>` | (Required if 2nd argument is present) The value for the filter specified by the 2nd argument. <br> - If 2nd argument is `proto`: an IP protocol number (e.g., `6` for TCP, `17` for UDP). <br> - If 2nd argument is `sip`: a source IP address (e.g., `192.168.1.10`). <br> - If 2nd argument is `dip`: a destination IP address (e.g., `8.8.8.8`). <br> - If 2nd argument is `dport`: a destination port number (e.g., `443`). |

##  Example usage
```
example_com:velocli> debug --nat_port_dump
SIP                     DIP  DPORT  PROTO   FREE  OFFSET  TAILQ  TOTAL  MISS  REFCNT
172.30.0.6   172.234.37.140    123     17  55534       1      0  55535     0       1
172.30.0.6   152.65.224.129    443      6  55517      18     15  55535     0       1
172.30.0.6       62.72.0.70    123     17  55534       1      0  55535     0       1
172.30.0.6   192.168.110.24    514     17  55534       1      0  55535     0       1
172.30.0.6          8.8.4.4     53     17  55532       3      0  55535     0       1
```
To filter for IPv4 UDP traffic:
```
example_com:velocli> debug --nat_port_dump v4 proto 17
```
To filter for all traffic to destination port 443:
```
example_com:velocli> debug --nat_port_dump all dport 443
```

##  Field descriptions
| Column | Description |
|---|---|
| `SIP` | Source IP address of the internal (LAN-side) host initiating the connection. This is the original IP address that is being NATted. |
| `DIP` | Destination IP address on the external (WAN-side) network that the internal host is communicating with. |
| `DPORT` | Destination Port on the `DIP` that the internal host is communicating with. |
| `PROTO` | IP Protocol number used for the session (e.g., `6` for TCP, `17` for UDP). |
| `FREE` | Number of available (free) source ports remaining in the port block associated with this NAT entry. |
| `OFFSET` | Number of source ports currently consumed (used) from the port block for this NAT entry. For a given entry, `OFFSET` + `FREE` typically equals `TOTAL`. |
| `TAILQ` | Internal system information, often related to queue management or linkage of NAT entries within system data structures. Generally used for diagnostic purposes. |
| `TOTAL` | Total size of the source port block associated with this NAT entry from which ports are allocated. |
| `MISS` | Count of misses during port allocation attempts for this NAT entry. This is an internal counter, potentially indicating port contention or near exhaustion if consistently high for new flows. |
| `REFCNT` | Reference count, indicating how many active flows or internal system references are currently associated with this specific NAT entry. |