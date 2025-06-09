#	--update_ra_host_config <interface> <subif_idx> <file_path>

##	Description
This command updates the Router Advertisement (RA) host configuration for a specified network interface and sub-interface using a configuration file. Router Advertisement is a mechanism used in IPv6 for hosts to discover routers and obtain network configuration parameters.

##  Arguments (required)
| Argument | Description |
|---|---|
| `<interface>` | The name of the network interface to configure (e.g., GE1, GE2). |
| `<subif_idx>` | The sub-interface index. For a primary interface without sub-interfaces, this is typically `0`. |
| `<file_path>` | The absolute path on the VeloCloud Edge to the file containing the RA host configuration settings. The format of this file is specific to the RA host configuration schema. |

##  Example usage
```
example_com:velocli> debug --update_ra_host_config GE1 0 /tmp/new_ra_config.json
```
This example updates the Router Advertisement host configuration for the primary interface `GE1` (sub-interface index `0`) using the configuration specified in the file `/tmp/new_ra_config.json` on the Edge.

##  Field descriptions
This command does not produce tabular output. Upon successful execution, it updates the RA host configuration on the specified interface. If an error occurs, an error message will be displayed.