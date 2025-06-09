# --nat_dump [orig | mod] [all | v4 | v6] [Filter list: type|proto|sip|sport|dip|dport|msip|mdip|msport|mdport|count]

## Description
Displays Network Address Translation (NAT) table information that has been synchronized from the active VeloCloud Edge. This command is typically used on a standby Edge in a High Availability (HA) configuration to inspect the NAT state received from the active peer.

## Arguments (optional)
The command can be run with or without arguments. Arguments are positional.
1.  **NAT Table View** (optional): Specifies whether to display original (pre-NAT) or modified (post-NAT) flow information.
2.  **IP Version Filter** (optional): Filters entries by IP version.
3.  **Filter Conditions** (optional): Further filters the output based on specific field values.

| Argument            | Description                                                                                                                                                              |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `orig`              | Display original (pre-NAT) NAT entries.                                                                                                                                  |
| `mod`               | Display modified (post-NAT) NAT entries.                                                                                                                                 |
| `all`               | Display NAT entries for all IP versions (IPv4 and IPv6). This is typically the default if an IP version filter is not specified.                                         |
| `v4`                | Display NAT entries for IPv4 only.                                                                                                                                       |
| `v6`                | Display NAT entries for IPv6 only.                                                                                                                                       |
| `filter_conditions` | One or more conditions to filter NAT entries. Filters can be applied using fields from the "Filter list": `type`, `proto`, `sip`, `sport`, `dip`, `dport`, `msip`, `mdip`, `msport`, `mdport`, `count`. The exact syntax for applying filters (e.g., `type SNAT`, `sip 1.2.3.4`) may depend on the specific implementation. |

## Example usage
```
example_com:velocli> debug --nat_dump
TYPE           OSIP            ODIP  OSPORT  ODPORT  OPROTO  OFLOW        MSIP            MDIP  MSPORT  MDPORT  MPROTO  MFLOW  SEGID  REFCNT
DNAT        1.2.3.4   170.85.14.130   34554    7000     TCP      0     1.2.3.4   165.225.34.43   34554      80     TCP      0      1       2
SNAT   192.168.88.1  152.65.224.129   10188     443     TCP      0  172.30.0.6  152.65.224.129   10005     443     TCP      0      0       2
DNAT        1.2.3.4   170.85.14.130   40072    7000     TCP      0     1.2.3.4   165.225.34.43   40072      80     TCP      0      1       2
DNAT        1.2.3.4   170.85.14.130   41814    7000     TCP      0     1.2.3.4   165.225.34.43   41814      80     TCP      0      1       2
SNAT   192.168.88.1         8.8.8.8   37373      53     UDP      0  172.30.0.6         8.8.8.8   10003      53     UDP      0      0       2
```

## Field descriptions
| Column | Description                                           |
|--------|-------------------------------------------------------|
| `TYPE`   | Type of NAT operation (e.g., `SNAT` for Source NAT, `DNAT` for Destination NAT). |
| `OSIP`   | Original Source IP address (pre-NAT).                 |
| `ODIP`   | Original Destination IP address (pre-NAT).            |
| `OSPORT` | Original Source Port (pre-NAT).                       |
| `ODPORT` | Original Destination Port (pre-NAT).                  |
| `OPROTO` | Original Protocol (e.g., TCP, UDP).                   |
| `OFLOW`  | Original Flow identifier.                             |
| `MSIP`   | Modified/Mapped Source IP address (post-NAT).         |
| `MDIP`   | Modified/Mapped Destination IP address (post-NAT).    |
| `MSPORT` | Modified/Mapped Source Port (post-NAT).               |
| `MDPORT` | Modified/Mapped Destination Port (post-NAT).          |
| `MPROTO` | Modified/Mapped Protocol (post-NAT).                  |
| `MFLOW`  | Modified/Mapped Flow identifier.                      |
| `SEGID`  | Segment ID associated with the NAT entry.             |
| `REFCNT` | Reference Count, indicating active use of the NAT entry. |