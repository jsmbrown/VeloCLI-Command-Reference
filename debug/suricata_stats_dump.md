# --suricata_stats_dump

## Description
Fetch stats from Suricata module. Suricata is an open-source network Intrusion Detection System (IDS), Intrusion Prevention System (IPS), and Network Security Monitoring (NSM) engine that may be integrated into the VeloCloud Edge. This command retrieves operational statistics from this module.

## Arguments (optional)
This command takes no arguments.

## Example usage
```
example_com:velocli> debug --suricata_stats_dump
{
  "event_type": "stats",
  "stats": {
    "app_layer": {
      "bytes": {
        "dcerpc": 0,
        // ... additional protocol byte counts and other app_layer stats follow
      },
      // ... other app_layer sub-categories like 'flow', 'pkts' follow
    },
    // ... other top-level stat categories like 'capture', 'decoder', 'detect', 'flow', 'tcp', 'memuse', 'uptime' follow
  }
  // ... other top-level fields like 'timestamp' may follow
}
```
**Note:** The example output above is a snippet. The actual output will be more extensive, detailing numerous statistics from various Suricata components.

## Field descriptions
The output is a JSON object containing statistics from the Suricata engine. The primary fields are described below:

| Field Path                 | Description                                                                                                |
|----------------------------|------------------------------------------------------------------------------------------------------------|
| `event_type`               | A string indicating the type of this message. For these statistics, it is "stats".                         |
| `stats`                    | A JSON object that serves as the main container for all Suricata statistics.                               |
| `stats.app_layer`          | An object containing statistics related to the analysis of application layer protocols (e.g., HTTP, DNS, TLS, SMB). |
| `stats.app_layer.bytes`    | An object within `stats.app_layer` that contains byte counts for traffic associated with various detected application layer protocols. |
| `stats.app_layer.bytes.dcerpc` | An example counter representing the number of bytes related to the DCERPC protocol. Similar entries will exist for other protocols monitored by Suricata. |

The `stats` object contains many other top-level categories, each providing detailed counters and metrics for different aspects of the Suricata engine, such as:
*   `capture`: Statistics related to packet capture.
*   `decoder`: Statistics on packet decoding events, layers, and errors.
*   `detect`: Statistics from the detection engine, including alerts triggered, rules loaded, and performance metrics.
*   `flow`: Statistics related to network flows tracked by Suricata.
*   `tcp`, `udp`, `icmp`: Statistics for specific transport and network layer protocols.
*   `memuse`: Memory usage statistics for various Suricata components.
*   `memcap`: Statistics related to configured memory caps.
*   `uptime`: The duration for which the Suricata engine has been running.
*   `output`: Statistics for output plugins (e.g., alert logging).

The specific fields and their nesting can be extensive, reflecting the comprehensive nature of Suricata's monitoring capabilities.