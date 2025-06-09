#	--show_edge_wss_conf

##	Description
Displays the current Web Security Service (WSS) configuration for the VeloCloud Edge. WSS is typically used to integrate with Cloud Security Services (CSS), such as Zscaler, for securing internet-bound traffic. This command allows administrators to verify the WSS settings applied to the Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --show_edge_wss_conf
[]

example_com:velocli> 
```

##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example output `[]` indicates that there is no Web Security Service (WSS) configuration currently active or defined on the Edge. If a WSS configuration were present, this command would display the specific parameters of that configuration (e.g., service FQDNs, PSK, tunnel details). |