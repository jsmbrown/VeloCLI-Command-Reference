# `debug --update_mgd_route`

## Description
This command toggles the routing preference for management traffic originating from the VeloCloud Edge. Management traffic, essential for communication with the VeloCloud Orchestrator (e.g., using VeloCloud Management Protocol - VCMP), can be configured to be sent either directly to the Orchestrator or proxied through a VeloCloud Gateway (GW). Executing this command switches the current preference to the alternative path. For instance, if management traffic is currently routed directly, this command will change the configuration to route it via a Gateway, and vice-versa.

## Arguments
This command does not take any arguments.

## Example Usage
The following example shows the command being executed and the resulting output, indicating that management traffic has been rerouted to a direct path.
```
example_com:velocli> debug --update_mgd_route
{
  "mgd_rerouted": "direct"
}
```
If the traffic was previously "direct", running the command again would likely result in:
```
example_com:velocli> debug --update_mgd_route
{
  "mgd_rerouted": "via GW"
}
```

## Field Descriptions
| Field          | Description                                                                                                                               |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `mgd_rerouted` | Indicates the new path to which the Edge's management traffic has been configured after executing the command. Possible values are:<ul><li>`direct`: Management traffic is now configured to be sent directly to the VeloCloud Orchestrator.</li><li>`via GW`: Management traffic is now configured to be sent via a VeloCloud Gateway.</li></ul> |