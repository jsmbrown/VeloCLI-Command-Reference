#	--session_table_summary

##	Description
Displays a summary of the session table, including counts of active and stale sessions. The session table tracks active network connections passing through the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --session_table_summary
{
  "error": "session table not initialized"
}
```
**Note:** The example output `{"error": "session table not initialized"}` indicates that the session table was not yet active or populated at the time the command was run. Under normal operating conditions with active traffic, this command would show counts of active and stale sessions.

##  Field descriptions
| Field | Description |
|---|---|
| error | If present, indicates an error condition encountered while trying to retrieve the session table summary. In the example, "session table not initialized" means the session tracking mechanism was not active or had no sessions to report. |
| active_sessions (expected) | The number of currently active user traffic sessions. (This field is expected in a successful output but not shown in the error example). |
| stale_sessions (expected) | The number of sessions that are no longer active but are still present in the table, awaiting timeout or cleanup. (This field is expected in a successful output but not shown in the error example). |