#	--nat_summary [orig | mod] [v4 | v6 | all] [Filter list: type|peer_id|seg|proto|sip|sport|dip|dport|msip|mdip]

##	Description
This command displays a summary of Network Address Translation (NAT) table entries, providing counts grouped by various criteria. It allows filtering based on whether the information is original (pre-NAT) or modified (post-NAT), IP version, and a list of specific NAT entry attributes.

##  Arguments (optional)
The arguments allow for filtering the NAT summary. They can be used in combination.

| Argument          | Description                                                                                                                                                                                                                            |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `orig` \| `mod`   | Specifies whether to display summary counts for original (pre-NAT) or modified (post-NAT) IP addresses and ports. If omitted, the default behavior may depend on the system or show a general summary.                                   |
| `v4` \| `v6` \| `all` | Filters the summary by IP version: `v4` for IPv4, `v6` for IPv6, or `all` for both. If omitted, `all` or a system default might be assumed.                                                                                             |
| Filter criteria   | Allows for more granular filtering of the NAT summary. You can specify one or more of the following filter fields. The exact syntax for applying values to these filters (e.g., `field=value`) would follow the specific field. Available filter fields include: `type`, `peer_id`, `seg` (segment ID), `proto` (protocol), `sip` (source IP), `sport` (source port), `dip` (destination IP), `dport` (destination port), `msip` (modified source IP), `mdip` (modified destination IP). |

##  Example usage
```
example_com:velocli> debug --nat_summary
PEER_ID                                SEG            IP  COUNT*
00000000-0000-0000-0000-000000000000     1       1.2.3.4      65
00000000-0000-0000-0000-000000000000     0  192.168.88.1       8

```

##  Field descriptions
| Column  | Description                                                                                                |
|---------|------------------------------------------------------------------------------------------------------------|
| PEER_ID | The identifier of the peer associated with the NAT entries. A value of `00000000-0000-0000-0000-000000000000` typically indicates local traffic or traffic not associated with a specific VeloCloud peer. |
| SEG     | The segment ID to which the NAT entries belong.                                                            |
| IP      | The IP address for which NAT entries are being summarized. This could be an original or modified IP depending on other arguments used. |
| COUNT*  | The number of NAT entries summarized for the corresponding PEER_ID, SEG, and IP. The asterisk (*) may denote specific conditions or types of counts; refer to system behavior for precise meaning. |