#	--netflow_intervals

##	Description
Displays the configured interval times, in seconds, for various Netflow table updates. This command is typically used within the verbose namespace for detailed debugging.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --netflow_intervals
{
  "app_table": 300,
  "flow_link_stats_table": 60,
  "flow_table": 60,
  "interface_table": 300,
  "link_table": 300
}
```

##  Field descriptions
| Field                     | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `app_table`               | The interval (in seconds) for updating the application identification table. |
| `flow_link_stats_table`   | The interval (in seconds) for updating the flow statistics per link table.  |
| `flow_table`              | The interval (in seconds) for updating the main flow table.                 |
| `interface_table`         | The interval (in seconds) for updating the interface statistics table.      |
| `link_table`              | The interval (in seconds) for updating the link quality and status table.   |