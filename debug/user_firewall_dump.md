#	--user_firewall_dump [all | seg-id] [all | src-ip] [all | src-port] [all | dest-ip] [all | dest-port] [max flows to display] [all | v4 | v6] [efs-rule] [allow | block]

##	Description
This command displays the current firewall entries for user traffic. It provides a detailed view of active network flows, including source and destination IP addresses, ports, protocols, application identification, TCP state, firewall rule applied, and traffic statistics. It also includes information related to Network Address Translation (NAT), Enhanced Firewall Services (EFS), Intrusion Detection and Prevention System (IDPS) actions, URL reputation and categorization, and malicious IP actions if applicable.

##  Arguments (optional)
| Argument                 | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `all` (or no argument)   | Display all firewall entries (subject to `max flows to display`).           |
| `seg-id`                 | Filter by a specific segment ID.                                            |
| `src-ip`                 | Filter by a specific source IP address.                                     |
| `src-port`               | Filter by a specific source port.                                           |
| `dest-ip`                | Filter by a specific destination IP address.                                |
| `dest-port`              | Filter by a specific destination port.                                      |
| `max flows to display`   | An integer specifying the maximum number of flow entries to display.        |
| `v4` \| `v6`             | Filter by IP version (IPv4 or IPv6). `all` displays both.                   |
| `efs-rule`               | Filter by a specific Enhanced Firewall Services rule ID or name.            |
| `allow` \| `block`       | Filter by the firewall action (allow or block).                             |

##  Example usage
```
example_com:velocli> debug --user_firewall_dump
SRC_IP                DEST_IP  SRC_PORT  DEST_PORT  PROTO  DSCP                            APP      TCP_STATE  RULE  BYTES_SENT  BYTES_RCVD  DURATION  LAN_SIDE_NAT  NAT_SIP  NAT_SPORT  NAT_DIP  NAT_DPORT  EFS_ACTION  IDPS_ACTION  SIGNATURE_ID  SEVERITY  URL_REP  URL_REP_ACTION  URL_CAT  URL_CAT_ACTION  MAL_IP_ACTION
1.2.3.4         170.85.14.130     41984       7000    TCP     0    HyperText Transfer Protocol        CLOSING   N/A       417 B       281 B       0 s           N/A      N/A        N/A      N/A        N/A         N/A          N/A           N/A       N/A      N/A             N/A      N/A             N/A            N/A
1.2.3.4         170.85.14.130     38392       7000    TCP     0    HyperText Transfer Protocol        CLOSING   N/A       417 B       281 B       0 s           N/A      N/A        N/A      N/A        N/A         N/A          N/A           N/A       N/A      N/A             N/A      N/A             N/A            N/A
1.2.3.4         170.85.14.130     41980       7000    TCP     0    HyperText Transfer Protocol        CLOSING   N/A       417 B       281 B       0 s           N/A      N/A        N/A      N/A        N/A         N/A          N/A           N/A       N/A      N/A             N/A      N/A             N/A            N/A
1.2.3.4         170.85.14.130     55964       7000    TCP     0    HyperText Transfer Protocol        CLOSING   N/A       417 B       281 B       0 s           N/A      N/A        N/A      N/A        N/A         N/A          N/A           N/A       N/A      N/A             N/A      N/A             N/A            N/A
1.2.3.4         170.85.14.130     60520       7000    TCP     0    HyperText Transfer Protocol        CLOSING   N/A       417 B       281 B       0 s           N/A      N/A        N/A      N/A        N/A         N/A          N/A           N/A       N/A      N/A             N/A      N/A             N/A            N/A
```

##  Field descriptions
| Column           | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `SRC_IP`         | Source IP address of the flow.                                              |
| `DEST_IP`        | Destination IP address of the flow.                                         |
| `SRC_PORT`       | Source port number of the flow.                                             |
| `DEST_PORT`      | Destination port number of the flow.                                        |
| `PROTO`          | Protocol used by the flow (e.g., TCP, UDP, ICMP).                           |
| `DSCP`           | Differentiated Services Code Point value for QoS.                           |
| `APP`            | Application identified for the flow.                                        |
| `TCP_STATE`      | Current state of the TCP connection (e.g., ESTABLISHED, CLOSING, TIME_WAIT). |
| `RULE`           | Firewall rule ID or name that matched this flow. `N/A` if no specific rule. |
| `BYTES_SENT`     | Total bytes sent from the source in this flow.                              |
| `BYTES_RCVD`     | Total bytes received by the source (sent by the destination) in this flow.  |
| `DURATION`       | Duration of the flow in seconds.                                            |
| `LAN_SIDE_NAT`   | Indicates if LAN-side NAT is applied (e.g., N/A, Source NAT, Dest NAT).     |
| `NAT_SIP`        | NATed Source IP address, if applicable.                                     |
| `NAT_SPORT`      | NATed Source Port, if applicable.                                           |
| `NAT_DIP`        | NATed Destination IP address, if applicable.                                |
| `NAT_DPORT`      | NATed Destination Port, if applicable.                                      |
| `EFS_ACTION`     | Action taken by Enhanced Firewall Services (e.g., Allow, Deny, N/A).        |
| `IDPS_ACTION`    | Action taken by the Intrusion Detection and Prevention System (e.g., Alert, Drop, N/A). |
| `SIGNATURE_ID`   | ID of the IDPS signature that was triggered, if any.                        |
| `SEVERITY`       | Severity level of the triggered IDPS signature (e.g., High, Medium, Low, N/A). |
| `URL_REP`        | URL Reputation score or status (e.g., N/A, Malicious, Suspicious).          |
| `URL_REP_ACTION` | Action taken based on URL reputation (e.g., Allow, Block, N/A).             |
| `URL_CAT`        | URL Category identified (e.g., Social Networking, News, N/A).               |
| `URL_CAT_ACTION` | Action taken based on URL category (e.g., Allow, Block, N/A).               |
| `MAL_IP_ACTION`  | Action taken due to malicious IP reputation (e.g., Block, N/A).             |