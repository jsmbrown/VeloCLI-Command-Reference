#	--ha_flow_dump [all | dest-ip]

##	Description
Dumps flow information that has been synchronized from the ACTIVE VeloCloud Edge to its STANDBY peer in a High Availability (HA) configuration. This command is typically executed on the STANDBY Edge to inspect the state of flows that would be maintained if a failover were to occur, ensuring session persistence.

##  Arguments (optional)
| Argument  | Description                                                                                                                               |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all`     | (Default) If no argument is specified, or if `all` is explicitly used, this option displays all synchronized flow information from the ACTIVE Edge. |
| `dest-ip` | Filters the output to display flow information only for the specified destination IP address. For example: `debug --ha_flow_dump 192.168.1.100`. |

##  Example usage
The following example shows the output when the HA flow synchronization table is not found. This might occur if the command is run on an Edge that is not currently acting as a standby in an HA pair, if the Edge is the ACTIVE unit, or if there are issues with HA synchronization:
```
example_com:velocli> debug --ha_flow_dump
{
  "error": "HA Flow sync table not found"
}
```
A successful execution of this command would list the synchronized flows, typically in a structured format (e.g., JSON), detailing active network sessions.

##  Field descriptions
A successful execution of this command would display details of the synchronized flows. While the exact output format and fields can vary, common information for each flow typically includes:

| Field                 | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Source IP Address     | The source IP address of the synchronized flow.                             |
| Destination IP Address| The destination IP address of the synchronized flow.                          |
| Source Port           | The source port number (e.g., for TCP or UDP protocols).                    |
| Destination Port      | The destination port number (e.g., for TCP or UDP protocols).                 |
| Protocol              | The network protocol of the flow (e.g., TCP, UDP, ICMP).                    |
| State                 | The current state of the flow (e.g., ESTABLISHED, TIME_WAIT for TCP flows). |
| Ingress Interface     | The interface on which the flow entered the ACTIVE Edge.                    |
| Egress Interface      | The interface on which the flow is expected to exit.                        |
| NAT Information       | Details of any Network Address Translation applied to the flow.             |
| Application ID        | Identifier for the application associated with the flow, if recognized.     |
| Timeout / Timers      | Remaining lifetime or other timers associated with the flow.                |
| Segment ID            | The segment to which the flow belongs.                                      |