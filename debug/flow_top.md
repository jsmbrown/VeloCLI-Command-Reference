#	--flow_top [<sort_column>|delay_secs=<secs>|max_flows=<num>]

##	Description
Displays the top active flows on the VeloCloud Edge. This command provides real-time insights into the most active traffic streams passing through the appliance, which can be useful for troubleshooting and monitoring network activity.

##  Arguments (optional)
The command can be run without arguments to show top flows with default settings. Arguments can be combined using the `|` (pipe) character.

| Argument | Description |
|---|---|
| `<sort_column>` | Specifies the column by which the flow data should be sorted. Common sort columns might include `packets`, `bytes`, `rate_bps`, etc. (The exact available column names would be evident from the command's output without this argument). |
| `delay_secs=<secs>` | Sets the delay in seconds for refreshing the top flow data. For example, `delay_secs=5` would refresh the display every 5 seconds. |
| `max_flows=<num>` | Limits the number of top flows displayed. For example, `max_flows=10` would show the top 10 flows. |

##  Example usage
To display the top flows with default settings:
```
example_com:velocli> debug --flow_top
```

To display the top 20 flows, sorted by bytes, and refreshing every 10 seconds (example of combined arguments):
```
example_com:velocli> debug --flow_top sort_column=bytes|max_flows=20|delay_secs=10
```
*(Note: The exact syntax for combining arguments and the specific sort column names should be verified with the command's help or by observing its behavior.)*

##  Field descriptions
The output fields for this command typically include details about each flow. While the exact columns can vary, common fields include:

| Column (Example)      | Description |
|-----------------------|-------------|
| Source IP             | The source IP address of the flow. |
| Source Port           | The source port of the flow. |
| Destination IP        | The destination IP address of the flow. |
| Destination Port      | The destination port of the flow. |
| Protocol              | The protocol used by the flow (e.g., TCP, UDP, ICMP). |
| Packets               | The number of packets transmitted in the flow. |
| Bytes                 | The number of bytes transmitted in the flow. |
| Rate (bps)            | The current data rate of the flow in bits per second. |
| Application           | The identified application associated with the flow. |
| Interface             | The interface through which the flow is passing. |
| Path                  | The SD-WAN path taken by the flow. |
| QoE                   | Quality of Experience metrics for the flow. |
*(The actual columns and their names will be displayed when the command is executed.)*