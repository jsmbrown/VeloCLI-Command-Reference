#	--udp_hole_punching

##	Description
Dumps diagnostic information related to the UDP hole punching process. UDP hole punching is a technique used in NAT traversal to establish a direct UDP connection between two peers behind NAT devices. This command helps in troubleshooting connectivity issues where UDP hole punching might be failing.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --udp_hole_punching
{
  "Error": "No Links Found"
}
```
The output above indicates that the system could not find any active links for which to display UDP hole punching probe data. In a scenario with active links and ongoing probes, the output would contain detailed information about the state of these probes.

##  Field descriptions
The output is a JSON object.
| Field | Description |
|---|---|
| Error | Describes an error encountered while trying to retrieve UDP hole punching data. In the example, it indicates that no network links were found. |