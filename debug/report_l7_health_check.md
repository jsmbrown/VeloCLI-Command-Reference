# --report_l7_health_check &lt;seg-id&gt; &lt;nvs-logical-id&gt; &lt;link-logical-id&gt; &lt;dest-id&gt; &lt;l7-success&gt; &lt;rtt_ms&gt;

## Description
The `debug --report_l7_health_check` command is used to manually report the results of a Layer 7 (L7) health check. This is typically utilized for diagnostic or testing purposes, allowing an administrator to simulate or inject health check status for a service. Such services are often associated with a Non-VeloCloud Site (NVS), also known as a Non-SD-WAN Destination (NSD), or a Cloud Security Service (CSS). The command requires parameters specifying the segment ID, NVS logical ID, link logical ID, destination ID, L7 success status, and the Round Trip Time (RTT) in milliseconds.

## Arguments
| Argument | Description |
|---|---|
| `<seg-id>` | The identifier of the VeloCloud segment associated with this L7 health check. Segments are used for network traffic isolation and policy enforcement. |
| `<nvs-logical-id>` | The logical identifier for the Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD) for which the health check is being reported. L7 health checks are commonly used to monitor the availability of services at these external sites. |
| `<link-logical-id>` | The logical identifier of the specific WAN link on the VeloCloud Edge over which the L7 health check was performed or is being reported for. |
| `<dest-id>` | An identifier for the specific destination service or endpoint that was the target of the L7 health check. This could be an internal ID mapping to a configured health check target (e.g., URL, application endpoint). |
| `<l7-success>` | A status flag indicating the outcome of the Layer 7 health check. This is typically `1` for success (or true) and `0` for failure (or false). |
| `<rtt_ms>` | The Round Trip Time in milliseconds measured for the L7 health check. This value indicates the latency to the destination service. |

## Example Usage
The command requires all arguments to be specified to report an L7 health check. If called without the required arguments, it will display usage information for the `debug.py` script.

**Scenario 1: Command called without arguments**
If the command is invoked without the necessary arguments, it displays a help message.
```
example_com:velocli> debug --report_l7_health_check
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
*(Note: The output above is a generic help message for the `debug.py` script, indicating that arguments are expected for the `report_l7_health_check` subcommand.)*

**Scenario 2: Command called with arguments to report a successful health check**
This example shows how to report a successful L7 health check for a service.
```
example_com:velocli> debug --report_l7_health_check 1 0a1b2c3d-4e5f-6a7b-8c9d-0e1f2a3b4c5d 3 27 1 45
```
*Output:*
This command is designed to report data into the system. Upon successful execution with valid arguments, it may produce minimal or no direct output to the CLI (e.g., a simple confirmation message or status code). The primary effect is the internal processing of the reported health check data by the VeloCloud Edge, which might influence routing decisions or status monitoring for the associated service.

## Field Descriptions
This command is used to input data (L7 health check results) into the system rather than to display tabular output. Therefore, a "Field Descriptions" section detailing output columns is not applicable for this command. The arguments listed in the "Arguments" section above define the data being reported.