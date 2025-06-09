#	--halfopen_dump

##	Description
This command dumps the table of half-open connection counts per destination IP address. Half-open connections are TCP connections for which the initial SYN packet has been sent, but the three-way handshake has not yet completed. This information is useful for monitoring potential SYN flood attacks or other network anomalies related to connection establishment. The output also indicates whether the stateful firewall's half-open limit is enabled for IPv4 and IPv6 traffic.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --halfopen_dump
Stateful Firewall Halfopen Limit : IPv4 : Disabled
                                   IPv6 : Disabled
====================== DESTINATION-IP LIST ====================
DESTINATION-IP   COUNT

example_com:velocli>
```

##  Field descriptions
| Column/Field | Description |
|---|---|
| Stateful Firewall Halfopen Limit : IPv4 | Indicates whether the limit on half-open TCP connections for IPv4 traffic is `Enabled` or `Disabled`. |
| Stateful Firewall Halfopen Limit : IPv6 | Indicates whether the limit on half-open TCP connections for IPv6 traffic is `Enabled` or `Disabled`. |
| DESTINATION-IP | The destination IP address for which half-open connection counts are being tracked. |
| COUNT | The number of half-open connections currently established towards the corresponding DESTINATION-IP. |