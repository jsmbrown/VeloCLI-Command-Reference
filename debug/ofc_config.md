#	--ofc_config

##	Description
Displays the current Overlay Flow Control (OFC) configuration active on the VeloCloud Edge. OFC determines how routing preference within the SD-WAN overlay is calculated, influencing path selection based on various metrics and policies.

##  Arguments (optional)
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --ofc_config
DCC: True
NSD OFC: True
RefreshVer: 1696001110202

Edge
	adv_static:1
```

##  Field descriptions
| Column       | Description                                                                                                                               |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| DCC          | Dynamic Cost Calculation. If `True`, the system dynamically adjusts path costs based on real-time network conditions for OFC decisions.     |
| NSD OFC      | Non-SD-WAN Destination Overlay Flow Control. If `True`, OFC mechanisms are applied to traffic destined for Non-SD-WAN Destinations (NSDs). |
| RefreshVer   | The timestamp (in Unix epoch milliseconds) indicating the last time the OFC configuration was refreshed or updated from the Orchestrator. |
| **Edge**     | This section contains OFC parameters specific to the Edge.                                                                                |
| adv_static   | Advertise Static Routes. If `1` (True), static routes configured on the Edge are advertised within the VeloCloud overlay for OFC purposes. |