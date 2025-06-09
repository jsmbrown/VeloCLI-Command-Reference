#	--ip_sla_dump

##	Description
This command dumps information related to IP Service Level Agreement (SLA) configurations. IP SLA is a feature used to measure network performance by sending test traffic between network devices. This command can help in troubleshooting and verifying IP SLA configurations on the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --ip_sla_dump
[
  {
    "probes": [],
    "responders": []
  }
]
```

##  Field descriptions
| Field | Description |
|---|---|
| probes | An array listing the configured IP SLA probes. Each probe entry would typically contain details about the specific test being performed, such as target IP, type of probe, frequency, etc. In the example, this array is empty, indicating no active probes. |
| responders | An array listing the configured IP SLA responders. Responders are devices configured to listen for and respond to IP SLA probe packets. In the example, this array is empty, indicating no active responders. |