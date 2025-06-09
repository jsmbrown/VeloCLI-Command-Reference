# --nat_port_restricted_dump [v4 | v6 | all] [Filter list: proto|inside_sip|inside_sport|outside_sip|outside_sport]

## Description
Dumps the current NAT (Network Address Translation) port-restricted cone NAT table. This table contains entries for active NAT sessions where an external host can only send packets to an internal host if the internal host had previously sent a packet to the external host's specific IP address and port.

## Arguments (optional)
The command can be run without arguments to display all entries. The following optional arguments can be used to filter the output:

| Argument Group/Syntax Element | Description |
|---|---|
| `v4 \| v6 \| all` | Specifies the IP version for the NAT entries to display: <br> - `v4`: Show only IPv4 NAT entries. <br> - `v6`: Show only IPv6 NAT entries. <br> - `all`: Show both IPv4 and IPv6 NAT entries. <br> If omitted, the command typically defaults to showing `all` or a pre-configured default (often IPv4). |
| `Filter list: proto\|inside_sip\|inside_sport\|outside_sip\|outside_sport` | This indicates that you can provide filter criteria as `field_name value` pairs. Multiple pairs can be specified to narrow down the results. <br> Valid `field_name`s are: <br> - `proto`: Filters by protocol (e.g., `TCP`, `UDP`). <br> - `inside_sip`: Filters by the inside (private) source IP address. <br> - `inside_sport`: Filters by the inside (private) source port. <br> - `outside_sip`: Filters by the outside (public/NATed) source IP address. <br> - `outside_sport`: Filters by the outside (public/NATed) source port. <br> **Example of filter usage:** `debug --nat_port_restricted_dump v4 proto TCP inside_sport 8080` |

## Example usage
```
example_com:velocli> debug --nat_port_restricted_dump
IN SIP   IN SPORT  OUT SIP  OUT SPORT  PROTO  IN USE  REFCNT

```
*(Note: The example output above only shows headers. A populated table would list active NAT entries.)*

## Field descriptions
The output table includes the following columns:

| Column      | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| `IN SIP`    | Inside Source IP Address. The original source IP address of the traffic from the internal (LAN-side) network. |
| `IN SPORT`  | Inside Source Port. The original source port of the traffic from the internal network.                     |
| `OUT SIP`   | Outside Source IP Address. The NATed (public-facing) source IP address used for the traffic on the external (WAN-side) network. |
| `OUT SPORT` | Outside Source Port. The NATed (public-facing) source port used for the traffic on the external network.   |
| `PROTO`     | Protocol. The transport layer protocol of the session (e.g., TCP, UDP).                                    |
| `IN USE`    | In Use. Indicates if the NAT mapping is currently active or in use (e.g., a flag or activity timer).       |
| `REFCNT`    | Reference Count. The number of active flows or connections currently utilizing this specific NAT mapping.    |