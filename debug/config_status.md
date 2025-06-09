#	--config_status

##	Description
Displays the current configuration version for various software modules running on the VeloCloud Edge. This command is useful for verifying that configuration updates pushed from the VeloCloud Orchestrator have been successfully applied to the Edge and to understand the recency and frequency of these updates.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##  Example usage
```
example_com:velocli> debug --config_status
module                    version  lastUpdate  updateCount
WAN                 1749032027358     7839461            2
QOS                 1747844194413     7839461            2
firewall            1747844159303     7839465            2
controlPlane        1749063164727     7839383            2
imageUpdate         1749038304133     7839384            2
```

##  Field descriptions
| Column | Description |
|---|---|
| module | The name of the specific software module or configuration area (e.g., WAN, QOS, firewall). |
| version | The current version identifier for the module's configuration. This is typically a timestamp or a unique sequence number representing the configuration state. |
| lastUpdate | An identifier or timestamp indicating when the last configuration update was processed for this module. |
| updateCount | The total number of times the configuration for this module has been updated since a baseline event (e.g., boot-up or last reset). |