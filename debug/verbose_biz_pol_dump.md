#	`--verbose_biz_pol_dump` `[all | segment-id]` `[all | policy-name]`

##	Description
This command provides a verbose dump of the current business policies configured on the VeloCloud Edge. Business policies are a core component of the VeloCloud SD-WAN solution, enabling granular control over how different types of traffic are routed and prioritized across the available WAN paths, including dynamic tunnels and connections to hubs or gateways.

##	Arguments (optional)
| Argument      | Description                                                                                                |
|---------------|------------------------------------------------------------------------------------------------------------|
| `segment-id`  | Optional. Filters the output to display policies for a specific segment ID. If omitted or set to `all`, policies for all segments are displayed. |
| `policy-name` | Optional. Filters the output to display a specific policy by its name. If omitted or set to `all`, all policies (matching the `segment-id` filter if provided) are displayed. |

If no arguments are provided, the command defaults to displaying all business policies for all segments.

##	Example usage
```
example_com:velocli> debug --verbose_biz_pol_dump
{
  "name": "BusinessPolicy",
  "policies": [
    {
      "allowConditionalBh": 0,
      "e2cRouteAction": {
        "action": "routeDirect",
        "dest": "internet",
        "enableNat": 1,
        "natPool": "Default",
        "natType": "interface",
        "preferredLink": "AUTO",
        "priority": "normal",
        "sla": {
          "fallbackAction": "AUTO",
          "jitter": 0,
          "latency": 0,
          "loss": 0,
          "monitorVoice": 0,
          "qoeTracking": 0,
          "slaClass": "DEFAULT_SLA"
        },
        "subLinks": []
      },
      "classifier": [
        {
          "appId": "any",
          "classId": 0,
          "dscp": "any",
          "group": "any",
          "host": "any",
          "maxPktSize": 0,
          "minPktSize": 0,
          "port": "any",
          "protocol": "any",
          "vlan": "any"
        }
      ],
      "defaultRule": 0,
      "displayName": "Internet Traffic",
      "enabled": 1,
      "id": 1,
      "linkSteering": {
        "distributeLoad": 0,
        "distribution": "AUTO",
        "mode": "AUTO",
        "primary": [],
        "secondary": [],
        "tertiary": []
      },
      "match": {
        "appId": [],
        "application": [],
        "classId": [],
        "dscp": [],
        "group": [],
        "host": [],
        "ipProtocol": [],
        "ipVersion": "any",
        "maxPktSize": 0,
        "minPktSize": 0,
        "other": [],
        "port": [],
        "sourceIp": [],
        "sourcePort": [],
        "vlan": []
      },
      "name": "Internet Traffic",
      "segmentId": 0,
      "serviceClass": "Default",
      "sla": {
        "fallbackAction": "AUTO",
        "jitter": 0,
        "latency": 0,
        "loss": 0,
        "monitorVoice": 0,
        "qoeTracking": 0,
        "slaClass": "DEFAULT_SLA"
      },
      "vnf": {
        "enabled": 0,
        "insertionPoint": "PRE_ROUTING",
        "serviceName": "",
        "serviceType": "NONE"
      }
    }
    // ... additional policies may be listed
  ]
}
```

##	Field descriptions
The output is in JSON format. The following describes key fields within the JSON structure:

| Field Path                      | Description                                                                                                                               |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `name`                          | The top-level object name, typically "BusinessPolicy".                                                                                    |
| `policies`                      | An array of objects, where each object represents a configured business policy.                                                           |
| `policies[].id`                 | A unique identifier for the business policy.                                                                                              |
| `policies[].name`               | The user-defined name of the business policy.                                                                                             |
| `policies[].displayName`        | The display name for the policy, often the same as `name`.                                                                                |
| `policies[].enabled`            | Indicates if the policy is currently active (`1` for enabled, `0` for disabled).                                                          |
| `policies[].segmentId`          | The segment ID to which this policy applies. `0` typically refers to the global segment.                                                  |
| `policies[].allowConditionalBh` | Indicates if Conditional Backhaul (CBH) is permitted for traffic matching this policy. `1` allows CBH, `0` disallows it.                   |
| `policies[].e2cRouteAction`     | An object defining the action for edge-to-cloud (e.g., internet or Cloud Security Service) traffic.                                       |
| `policies[].e2cRouteAction.action` | Specifies the routing action, e.g., `routeDirect` for direct internet access, `routeViaCss` for Cloud Security Service.                 |
| `policies[].e2cRouteAction.dest` | The destination type, e.g., `internet`.                                                                                                   |
| `policies[].classifier`         | An array defining the traffic matching criteria based on legacy classifier parameters.                                                    |
| `policies[].match`              | An object defining the detailed traffic matching criteria for the policy, such as application, IP address, port, DSCP values, etc.         |
| `policies[].match.application`  | An array of application names or IDs to match.                                                                                            |
| `policies[].match.sourceIp`     | An array of source IP addresses or subnets to match.                                                                                      |
| `policies[].linkSteering`       | An object defining how traffic matching this policy is steered across available WAN links (paths).                                        |
| `policies[].linkSteering.mode`  | The link steering mode, e.g., `AUTO`, `PREFERRED`, `MANDATORY`.                                                                           |
| `policies[].serviceClass`       | The Quality of Service (QoS) class assigned to traffic matching this policy.                                                              |
| `policies[].sla`                | An object defining the Service Level Agreement (SLA) requirements for traffic, including thresholds for latency, loss, and jitter.        |
| `policies[].sla.slaClass`       | The predefined SLA class associated with this policy.                                                                                     |
| `policies[].vnf`                | An object defining settings related to Virtual Network Function (VNF) service chaining for traffic matching this policy.                  |
| `policies[].vnf.enabled`        | Indicates if VNF service chaining is enabled for this policy.                                                                             |
| `policies[].defaultRule`        | Indicates if this is a default rule (`1` for true, `0` for false).                                                                        |