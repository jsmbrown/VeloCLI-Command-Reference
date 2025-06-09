# --client_connector {status | dump [info|ip|status|version] | restart | set_max_cpu_percent <percent_value>}

## Description
Manages the Client Connector service on the VeloCloud Edge. This command allows for retrieving status, dumping diagnostic information, restarting the service, and configuring its maximum CPU usage. The "Client Connector" typically refers to a feature enabling end-user devices or remote clients to connect to the SD-WAN fabric via the Edge.

## Arguments
The `--client_connector` command requires one of the following subcommands:

| Subcommand            | Parameter / Options                | Description                                                                                                |
|-----------------------|------------------------------------|------------------------------------------------------------------------------------------------------------|
| `status`              | N/A                                | Displays the current operational status of the Client Connector service.                                   |
| `dump`                | `[info | ip | status | version]` (optional) | Dumps diagnostic information for the Client Connector. Specific types of information can be requested using the optional parameters: `info` (general information), `ip` (IP configuration/state), `status` (detailed status), or `version` (component version). If no parameter is specified, it may dump a default or comprehensive set of information. |
| `restart`             | N/A                                | Restarts the Client Connector service on the Edge.                                                         |
| `set_max_cpu_percent` | `<percent_value>` (required)       | Sets the maximum CPU utilization percentage for the Client Connector service. `<percent_value>` is an integer (e.g., `50` for 50%). This can be used to limit the resources consumed by the Client Connector process. |

## Example usage
If run without a subcommand, `debug --client_connector` displays usage information:
```
example_com:velocli> debug --client_connector
Need atleast 1 argument.
Usage: debug.py --client_connector dump [info, ip, status, version]
       debug.py --client_connector restart
       debug.py --client_connector status
       debug.py --client_connector set_max_cpu_percent <percent_value>
```

Correct usage examples:
```
example_com:velocli> debug --client_connector status
# Output: Displays the current status of the Client Connector.
# (Actual output format will vary based on implementation)

example_com:velocli> debug --client_connector dump ip
# Output: Dumps IP-related diagnostic information for the Client Connector.
# (Actual output format will vary based on implementation)

example_com:velocli> debug --client_connector restart
# Output: Typically no direct output, or a confirmation message.
# Subsequent 'status' checks would reflect the restart.

example_com:velocli> debug --client_connector set_max_cpu_percent 60
# Output: Typically no direct output, or a confirmation message.
# The new CPU limit will be applied to the Client Connector service.
```

## Field descriptions
The output fields vary based on the subcommand used (`status`, `dump [option]`). Since specific output examples are not provided in the input, detailed field descriptions cannot be listed. Generally:
*   **status**: Output will likely contain fields describing the operational state, uptime, connected client counts (if applicable), and resource usage of the Client Connector service.
*   **dump [option]**: Output will contain various diagnostic details depending on the option specified:
    *   `info`: General configuration and state parameters.
    *   `ip`: IP addresses, routing information, or network interface details relevant to the Client Connector.
    *   `status`: More verbose status details than the main `status` subcommand.
    *   `version`: Software version of the Client Connector component.
*   **restart**: This command typically does not produce detailed field output, but might return a success/failure message.
*   **set_max_cpu_percent**: This command typically does not produce detailed field output, but might return a success/failure message. The effect can be observed through system monitoring tools or potentially reflected in `status` or `dump` outputs.