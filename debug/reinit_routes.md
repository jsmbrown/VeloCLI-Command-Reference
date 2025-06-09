#	--reinit_routes [all | segment-id]

##	Description
This command requests a route initialization for a specified segment or all segments. This action forces a synchronization of routes within the specified segment(s) to and from all connected VeloCloud Gateways. This can be useful to ensure route consistency across the SD-WAN fabric, particularly after network changes or to troubleshoot routing discrepancies.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no argument is provided) Requests route initialization for all configured segments on the VeloCloud Edge. |
| `segment-id` | A specific numerical identifier for the segment for which route initialization is requested. This will sync routes only for this particular segment. |

##  Example usage
```
example_com:velocli> debug --reinit_routes
{
  "Route_init": "requested"
}
```
Requesting route re-initialization for a specific segment (e.g., segment 1):
```
example_com:velocli> debug --reinit_routes 1
{
  "Route_init": "requested for segment 1"
}
```

##  Field descriptions
| Column | Description |
|---|---|
| `Route_init` | Indicates the status of the route initialization request. "requested" means the command to re-initialize routes for all segments (or the specified segment) has been successfully issued to the system. If a specific segment ID was provided, the message will reflect that. |