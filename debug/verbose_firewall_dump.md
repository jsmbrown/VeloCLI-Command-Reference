# `debug --verbose_firewall_dump [all | segment-id] [v4 | v6 | all]`

## Description
This command provides a verbose dump of the current firewall version and all configured policies on the VeloCloud Edge. It allows administrators to inspect the detailed state of the firewall, including rules, NAT configurations, and other security settings. This is particularly useful for troubleshooting firewall-related issues and verifying policy enforcement.

## Arguments (optional)
| Argument         | Description                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `[all | segment-id]` | Optional. Specifies the segment ID for which to dump firewall policies. If 'all' is used or the argument is omitted, policies for all segments are displayed. |
| `[v4 | v6 | all]`  | Optional. Specifies the IP version of firewall policies to dump (IPv4 or IPv6). If 'all' is used or the argument is omitted, policies for both IP versions are displayed. |

## Example usage
```
example_com:velocli> debug --verbose_firewall_dump
{
  "firewall": [
    {
      "efs_enabled": true,
      "efs_features": {
        "idps": true,
        "url_filtering": false,
        "ssl_proxy": false,
        "av": false,
        "sandbox": false
      },
      "version": 1695790000,
      "stateful_firewall_rules": [
        {
          "name": "Allow LAN to Internet",
          "match": {
            "source_ip": "any",
            "destination_ip": "any",
            "application": "any",
            "source_zone": "LAN",
            "destination_zone": "INTERNET"
          },
          "action": "allow",
          "logging_enabled": true
        }
        // ... additional rules and policies
      ],
      "nat_rules": [
        // ... NAT rule configurations
      ]
      // ... other firewall configurations for this segment/context
    }
    // ... configurations for other segments if applicable
  ],
  "system_firewall_version": "1.2.3",
  "last_updated_timestamp": "2023-09-27T05:45:00Z"
  // The actual output will be much more extensive and detailed.
}
```

## Field descriptions
The output is a JSON object containing a comprehensive dump of the firewall configuration. The structure and fields can be extensive. Below are descriptions for some common top-level and nested fields based on the example.

| Field                          | Description                                                                                                                               |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `firewall`                     | An array of objects, where each object typically represents the firewall configuration for a specific segment or context on the Edge.       |
| `firewall[].efs_enabled`       | Boolean. Indicates if the Edge Firewall Service (EFS), which may encompass VNF-based firewall capabilities, is enabled for this context. |
| `firewall[].efs_features`      | An object detailing specific advanced security features enabled within the Edge Firewall Service.                                         |
| `firewall[].efs_features.idps` | Boolean. Indicates if Intrusion Detection and Prevention System (IDPS) is enabled.                                                        |
| `firewall[].efs_features.url_filtering` | Boolean. Indicates if URL filtering is enabled.                                                                                  |
| `firewall[].efs_features.ssl_proxy` | Boolean. Indicates if SSL Proxy (for inspecting encrypted traffic) is enabled.                                                      |
| `firewall[].efs_features.av`   | Boolean. Indicates if Anti-Virus scanning is enabled.                                                                                     |
| `firewall[].efs_features.sandbox` | Boolean. Indicates if sandboxing for unknown threats is enabled.                                                                          |
| `firewall[].version`           | A version identifier or timestamp for the firewall policy set applied to this context/segment.                                            |
| `firewall[].stateful_firewall_rules` | An array of objects, each defining a stateful firewall rule.                                                                            |
| `firewall[].stateful_firewall_rules[].name` | A user-defined name for the firewall rule.                                                                                      |
| `firewall[].stateful_firewall_rules[].match` | An object specifying the criteria for traffic to match this rule (e.g., source/destination IP, application, zone).              |
| `firewall[].stateful_firewall_rules[].match.source_ip` | The source IP address or prefix for the rule match.                                                                     |
| `firewall[].stateful_firewall_rules[].match.destination_ip` | The destination IP address or prefix for the rule match.                                                              |
| `firewall[].stateful_firewall_rules[].match.application` | The application or service identifier for the rule match.                                                               |
| `firewall[].stateful_firewall_rules[].match.source_zone` | The source zone (e.g., LAN, WAN, specific VLAN segment) for the rule match.                                               |
| `firewall[].stateful_firewall_rules[].match.destination_zone` | The destination zone for the rule match.                                                                                |
| `firewall[].stateful_firewall_rules[].action` | The action to take if traffic matches the rule (e.g., "allow", "deny").                                                       |
| `firewall[].stateful_firewall_rules[].logging_enabled` | Boolean. Indicates if logging is enabled for traffic matching this rule.                                                  |
| `firewall[].nat_rules`         | An array of objects, each defining a Network Address Translation (NAT) rule.                                                              |
| `system_firewall_version`      | A string indicating the overall version of the firewall software or engine running on the Edge.                                           |
| `last_updated_timestamp`       | An ISO 8601 timestamp indicating when the firewall configuration was last updated or synchronized from the VeloCloud Orchestrator.        |

**Note:** The actual output can be very verbose and may include many other fields related to different aspects of the firewall configuration, such as NAT policies, security zones, application identification details, and VNF-specific settings if applicable. The fields listed above are illustrative.