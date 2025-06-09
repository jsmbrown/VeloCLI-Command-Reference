#	--ip_threat_lookup

##	Description
Fetch IP threat score for a given IP. This command queries an external or internal threat intelligence database, potentially integrated with the VeloCloud Orchestrator or a partner Cloud Security Service (CSS), to retrieve the risk score and associated threat details for the specified IP address. This information is valuable for network administrators to assess potential security risks from IPs interacting with the VeloCloud Edge or the broader SD-WAN fabric.

##	Arguments
| Argument    | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `IP_ADDRESS`  | **Required.** The IPv4 or IPv6 address for which to fetch the threat score. This argument must be provided positionally after the command. |

##	Example Usage
The example below shows the output when the `debug --ip_threat_lookup` command is run without the required `IP_ADDRESS` argument. This typically results in the display of the general help message for the `debug.py` script.

```
example_com:velocli> debug --ip_threat_lookup
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

To correctly use this command, provide an IP address as an argument:
```
example_com:velocli> debug --ip_threat_lookup 8.8.8.8
```
*(Note: The actual output for a successful command invocation is not provided in the input for this documentation.)*

##	Field Descriptions
Not applicable for the provided example output, as it shows a help message due to a missing required argument. A successful execution of this command would typically display fields related to the IP threat assessment, such as:

*   **IP Address:** The IP address that was queried.
*   **Threat Score:** A numerical or qualitative score representing the perceived risk level associated with the IP.
*   **Threat Category:** Classification of the threat (e.g., malware, phishing, command and control, spam).
*   **Reputation:** General reputation of the IP address (e.g., good, suspicious, malicious).
*   **Source Database:** The threat intelligence source or database that provided the information.
*   **Last Checked/Updated:** Timestamp indicating when the threat information was last updated or verified.