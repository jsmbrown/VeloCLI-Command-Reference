#	--add_routes [path to input routes json]

##	Description
This command allows a user to inject Border Gateway Protocol (BGP) routes directly into the VeloCloud Edge's Routing Information Base (RIB) and subsequently into the Forwarding Information Base (FIB). The routes to be added are specified in a JSON formatted file. This functionality is primarily intended for debugging, testing specific routing scenarios, or simulating BGP learned routes without requiring an active BGP peering session.

##	Arguments
| Argument | Description |
|---|---|
| `[path to input routes json]` | **Required.** The full filesystem path to a JSON file containing the definitions of the BGP routes to be added. The file must be accessible by the VeloCloud Edge. |

## JSON File Format
The input JSON file must contain an array of route objects. Each object in the array represents a single BGP route and should define its attributes. While the exact structure and supported attributes can be specific to the `debug.py` script version, a typical route object might include the following:

**Example `bgp_routes_to_add.json`:**
```json
[
  {
    "prefix": "192.168.200.0/24",
    "nexthop": "10.10.10.1",
    "as_path": "65001 65002",
    "origin": "IGP",
    "local_pref": 150,
    "med": 50,
    "communities": ["65001:100", "no-export"],
    "segment_id": 1
  },
  {
    "prefix": "2001:db8:cafe::/48",
    "nexthop": "2001:db8:10::1",
    "as_path": "65003",
    "origin": "INCOMPLETE",
    "segment_id": 1
  }
]
```
*Note: The precise JSON field names, accepted values, and mandatory fields should be verified against the specific implementation or internal documentation if available, as this example provides a general structure.*

##	Example Usage
To add BGP routes defined in a file named `my_custom_routes.json` located in the `/tmp/` directory on the VeloCloud Edge:
```
example_com:velocli> debug --add_routes /tmp/my_custom_routes.json
```
If the command is executed without the required path to the JSON file, it will typically display usage information for the `debug.py` script, similar to the following:
```
example_com:velocli> debug --add_routes
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ... (other debug options) ...
```

##	Field Descriptions
This command does not produce a tabular output of fields. Instead, its execution will result in one of the following:
*   **Success:** A confirmation message may be displayed indicating that the routes from the JSON file have been processed and attempts were made to add them to the RIB/FIB. The actual presence and state of these routes should then be verified using other commands (e.g., `debug --routes`).
*   **Error:** An error message will be displayed if:
    *   The specified JSON file cannot be found or accessed.
    *   The JSON file is malformed or does not conform to the expected structure.
    *   There is an internal error preventing the addition of the routes.