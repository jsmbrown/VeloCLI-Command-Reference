# --load_local_config

## Description
This command instructs the VeloCloud Edge to load its configuration from the `/root/config.json` file. This is typically used for specific troubleshooting or recovery scenarios where the Edge's configuration needs to be manually restored or applied from a local file, bypassing the standard configuration push from the VeloCloud Orchestrator.

## Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

## Example usage
```
example_com:velocli> debug --load_local_config
RPC error:  Error calling remote procedure: Internal error
```
**Note:** The example output shows an "RPC error". This indicates that the command execution encountered an issue. In a successful scenario, the command would execute without an error message, and the Edge would attempt to apply the configuration from `/root/config.json`. The error could be due to various reasons, such as the file not existing, being malformed, or internal system issues.