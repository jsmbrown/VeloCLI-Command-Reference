#	--vpn_test [seg-id|all]

##	Description
Performs a segment-aware VPN test. This test helps in verifying VPN connectivity and functionality within specific network segments or across all segments. The VeloCloud SD-WAN solution uses segments to isolate and manage network traffic, and this command allows administrators to ensure VPN tunnels are correctly established and operational for the intended segments.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `seg-id` | Specifies the ID of the network segment for which the VPN test should be performed. This allows for targeted testing of VPN connectivity for a particular segment. |
| `all` | Performs the VPN test across all configured network segments. This is useful for a comprehensive check of VPN status. |
| `none` | If no argument is provided, the behavior might default to testing a specific segment (e.g., the default segment) or all segments. The example usage shows it being run without arguments. |

##  Example usage
```
example_com:velocli> debug --vpn_test
```
*(Note: The output of this command is not provided in the example. The output would typically show the status and results of the VPN test, indicating success or failure, and potentially details about tunnel status, connectivity to peers, etc., for the specified segment(s).)*

##  Field descriptions
| Column | Description |
|---|---|
|   |  *(Output fields for this command are not available in the provided example. Documentation will be updated when field information is available.)* |