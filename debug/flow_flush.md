# --flow_flush [flow-id]

## Description
Flushes entries from the VeloCloud Edge's flow table. This command can be used to clear all active flows or a specific flow identified by its `flow-id`. When a `flow-id` is provided, only that particular flow entry is removed. If no `flow-id` is specified, all current flow entries are flushed from the table. This is useful for troubleshooting network connectivity issues or forcing a re-evaluation of traffic handling by the Edge.

## Arguments (optional)
| Argument  | Description                                                                                                                               |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `flow-id` | The unique identifier of a specific flow to be flushed. If this argument is omitted, all current flow entries in the flow table will be flushed. |

## Example usage
To flush all current flow table entries:
```
example_com:velocli> debug --flow_flush
{
  "ALERT": "Flow cleaned up"
}
```
*(Note: To flush a specific flow, you would provide its ID, e.g., `debug --flow_flush <specific_flow_id>`)*

## Field descriptions
The command returns a JSON object containing the following field:

| Field   | Description                                                                                                                                                              |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ALERT` | A confirmation message indicating the result of the flow flush operation. In the provided example, `"Flow cleaned up"` signifies that all flows were successfully flushed because no specific `flow-id` was provided. If a specific flow ID were targeted and successfully flushed, the message would typically reflect that. |