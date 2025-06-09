#	`--l7_health_checks`

##	Description
This command displays all currently configured Layer 7 health checks for Zscaler Cloud Security Services (CSS). These health checks are used by the VeloCloud Edge to monitor the availability and responsiveness of Zscaler proxy nodes, ensuring that internet-bound traffic is routed to healthy service instances.

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --l7_health_checks
[
  {
    "cloud": "zscalerthree.net",
    "destId": 0,
    "dstPort": 7000,
    "enterpriseLogicalId": "00000000-0000-0000-0000-000000000000"
  }
]
```

##  Field descriptions
| Column                | Description                                                                                                |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| `cloud`               | The domain name of the Zscaler cloud (e.g., `zscalerthree.net`) to which the L7 health check is targeted.    |
| `destId`              | An internal destination identifier used by the VeloCloud system for this specific Zscaler health check.      |
| `dstPort`             | The destination port number on the Zscaler node used for the L7 health check probe.                        |
| `enterpriseLogicalId` | The unique logical identifier for the enterprise associated with this Zscaler health check configuration.    |