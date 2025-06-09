#	--route_event_stats [all | logical_id]

##	Description
This command requests route event statistics. Route events are changes in the routing table, such as new routes being learned, existing routes being withdrawn, or changes in route attributes. These statistics can be requested for all peers or for a specific peer identified by its `logical_id`.

##  Arguments (optional)
| Argument | Description |
|---|---|
| all | Requests route event statistics for all peers connected to this VeloCloud Edge. This is the default if no argument is provided. |
| logical_id | The unique identifier (Logical ID) of a specific peer VeloCloud Edge or Gateway. Requesting with a `logical_id` will show route event statistics pertaining only to that peer. |

##  Example usage
```
example_com:velocli> debug --route_event_stats
RPC error:  Error calling remote procedure: Internal error

example_com:velocli> debug --route_event_stats 3294602a-5a69-4694-a7d2-811aff737faa
RPC error:  Error calling remote procedure: Internal error
```
*(Note: The example output shows an "RPC error". This indicates an issue encountered while trying to retrieve the statistics, possibly due to the feature state or an internal system issue at the time of command execution. Expected output would typically be a table or list of statistics related to route advertisements, withdrawals, and updates.)*

##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example provided resulted in an error, so field descriptions cannot be detailed. Typically, output would include counts of different types of route events (e.g., advertisements, withdrawals, updates) and potentially timestamps or peer identifiers associated with these events. |