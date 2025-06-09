#	--diag_trigger

##	Description
This command triggers the generation of a diagnostic bundle on the VeloCloud Edge. Diagnostic bundles contain logs, configuration details, and system status information that can be used for troubleshooting purposes. The bundle is typically uploaded to the VeloCloud Orchestrator for analysis.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --diag_trigger
null

example_com:velocli>
```
##  Field descriptions
| Column | Description |
|---|---|
| N/A | The command output `null` indicates the diagnostic trigger was initiated. The actual diagnostic bundle generation and upload happens in the background. Status of bundle generation can be monitored via the VeloCloud Orchestrator. |