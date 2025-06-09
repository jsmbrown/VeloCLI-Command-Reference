#	--del_routes &lt;path_to_input_routes_json&gt; &lt;fib|all&gt;

##	Description
Manually deletes Border Gateway Protocol (BGP) routes from the VeloCloud Edge's Routing Information Base (RIB) and/or Forwarding Information Base (FIB). This command is typically used for troubleshooting or specific network adjustment scenarios to remove BGP routes that were learned by the Edge. The routes to be deleted are specified in an input JSON file.

This command requires two positional arguments: the path to a JSON file detailing the routes to be deleted, and a keyword specifying whether to delete from the FIB or from both RIB and FIB.

##  Arguments
| Argument | Description |
|---|---|
| `&lt;path_to_input_routes_json&gt;` | **Required.** The full file path to a JSON-formatted file. This file must contain the definitions of the BGP routes that are targeted for deletion. The specific structure of this JSON file is critical for the command to correctly identify and process the routes. For example: `/tmp/routes_to_delete.json`. |
| `&lt;fib|all&gt;` | **Required.** Specifies the scope of the deletion operation. This must be one of the literal strings `fib` or `all`: <br> - `fib`: Deletes the specified BGP routes only from the Forwarding Information Base (FIB). The routes might still exist in the RIB and could potentially be re-advertised or re-inserted into the FIB based on BGP policies or subsequent updates. <br> - `all`: Deletes the specified BGP routes from both the Routing Information Base (RIB) and the Forwarding Information Base (FIB). This ensures a more comprehensive removal of the route from the Edge's BGP tables. |

##  Example usage
The following example shows the output when `debug --del_routes` is run without the required arguments. The system displays the help message for the `debug.py` script, indicating that arguments are expected for the `--del_routes` option.
```
example_com:velocli> debug --del_routes
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
To correctly use the command, you would provide the path to the JSON file and the scope (either `fib` or `all`). For example:
```
example_com:velocli> debug --del_routes /opt/vc/data/routes_for_deletion.json all
```
**Note:** The output for a successful execution is typically a status message (e.g., confirming the number of routes deleted) and is not shown in the example above. Ensure the specified JSON file exists on the Edge's filesystem and is correctly formatted.

##  Field descriptions
| Column | Description |
|---|---|
|   |  This command, when executed successfully with the required arguments, does not produce tabular output with specific columns. It typically outputs a status message indicating the success or failure of the route deletion process (e.g., "Successfully deleted X routes from FIB/RIB"). The example usage provided above demonstrates the help text displayed when the command is invoked without its mandatory arguments. |