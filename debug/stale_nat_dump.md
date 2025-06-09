#	--stale_nat_dump

##	Description
This command dumps the list of stale Network Address Translation (NAT) entries currently held by the VeloCloud Edge. Stale NAT entries are those that are no longer active but have not yet been timed out or cleared from the NAT table. This information can be useful for troubleshooting NAT-related connectivity issues or understanding NAT table utilization.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --stale_nat_dump
TYPE   OSIP  ODIP  OSPORT  ODPORT  OPROTO  MSIP  MDIP  MSPORT  MDPORT  MPROTO  SEGID  REFCNT

example_com:velocli>
```

##  Field descriptions
| Column  | Description                                          |
|---------|------------------------------------------------------|
| `TYPE`  | The type of NAT entry.                               |
| `OSIP`  | Original Source IP address of the flow.              |
| `ODIP`  | Original Destination IP address of the flow.         |
| `OSPORT`| Original Source Port of the flow.                    |
| `ODPORT`| Original Destination Port of the flow.               |
| `OPROTO`| Original Protocol of the flow (e.g., TCP, UDP, ICMP).|
| `MSIP`  | Mapped (post-NAT) Source IP address.                 |
| `MDIP`  | Mapped (post-NAT) Destination IP address.            |
| `MSPORT`| Mapped (post-NAT) Source Port.                       |
| `MDPORT`| Mapped (post-NAT) Destination Port.                  |
| `MPROTO`| Mapped (post-NAT) Protocol.                          |
| `SEGID` | The Segment ID associated with the NAT entry.        |
| `REFCNT`| Reference count for the NAT entry.                   |