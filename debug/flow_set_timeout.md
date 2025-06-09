# --flow_set_timeout [protocol] [Timeout in seconds]

## Description
Set the idle timeout value for network flows on the VeloCloud Edge. This command allows administrators to define how long a flow can remain idle before it is removed from the Edge's flow table. Configuring appropriate timeout values helps manage system resources and the size of the state table, particularly in environments with numerous connections.

## Arguments
| Argument             | Description                                                                                                |
|----------------------|------------------------------------------------------------------------------------------------------------|
| `[protocol]`         | Specifies the network protocol for which the idle timeout is being set (e.g., TCP, UDP, ICMP).             |
| `[Timeout in seconds]` | The duration in seconds that a flow for the specified protocol can be idle before it is timed out and removed. |

## Example usage
If the command `debug --flow_set_timeout` is entered without the required `[protocol]` and `[Timeout in seconds]` arguments, the system may display the general usage help for the `debug.py` script, as shown below:
```
example_com:velocli> debug --flow_set_timeout
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

A correct invocation to set the idle timeout for TCP flows to 3600 seconds (1 hour) would be:
```
example_com:velocli> debug --flow_set_timeout TCP 3600
```
To set the idle timeout for UDP flows to 300 seconds (5 minutes):
```
example_com:velocli> debug --flow_set_timeout UDP 300
```

## Field descriptions
| Column | Description |
|---|---|
| N/A    | This command is used to configure a system parameter and does not produce tabular output. Upon successful execution, it modifies the flow timeout setting. |