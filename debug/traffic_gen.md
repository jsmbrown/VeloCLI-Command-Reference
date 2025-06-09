#	--traffic_gen

##	Description
The `debug --traffic_gen` command is used to initiate a network traffic generation process on the VeloCloud Edge. This tool is typically used for testing and diagnostic purposes, allowing administrators to simulate network load or specific traffic patterns. The command attempts to load its operational parameters from a configuration file located at `/opt/vc/etc/traff_gen.json`. If this file is not present or improperly configured, the command will output an error.

##  Arguments (optional)
This command does not accept any arguments. It relies on the `/opt/vc/etc/traff_gen.json` file for its configuration.

##  Example usage
The following example demonstrates the output when the traffic generation configuration file is missing:
```
example_com:velocli> debug --traffic_gen
Loading parameters from /opt/vc/etc/traff_gen.json
Error: could not find config file /opt/vc/etc/traff_gen.json
```

##  Field descriptions
The command output in the provided example indicates an error state and does not produce a table with specific fields. The output messages are:
| Message | Description |
|---|---|
| `Loading parameters from /opt/vc/etc/traff_gen.json` |  Indicates the system is attempting to read the configuration for the traffic generator. |
| `Error: could not find config file /opt/vc/etc/traff_gen.json` | Signifies that the necessary configuration file for the traffic generator was not found at the specified path. |