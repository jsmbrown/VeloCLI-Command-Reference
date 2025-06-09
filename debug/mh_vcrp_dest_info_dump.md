#	--mh_vcrp_dest_info_dump

##	Description
This command dumps information about all VeloCloud Routing Protocol (VCRP) destinations, including details about their subscribers. VCRP is a proprietary routing protocol used within the VeloCloud SD-WAN overlay to exchange reachability information between VeloCloud Edges and Gateways.

##  Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --mh_vcrp_dest_info_dump
{
  "Error": "No destinations found"
}

example_com:velocli>
```
*Note: The example above shows the output when no VCRP destinations are found. If destinations exist, the output will be a JSON object detailing each destination and its subscribers.*

##  Field descriptions
| Field | Description |
|---|---|
| Error | This field will only appear if there is an issue retrieving the destination information or if no destinations are found. It provides a textual description of the error. |
| *(Other Fields)* | *When VCRP destinations are present, the JSON output will contain various fields detailing the destination ID, type, subscribers, and other VCRP-specific attributes. The exact structure will depend on the configured destinations.* |