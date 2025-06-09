#	--clock_sync

##	Description
Dumps the current clock synchronization state of the VeloCloud Edge. This command is useful for troubleshooting time synchronization issues, which can impact various system functionalities including tunnel establishments and logging. The output indicates whether the Edge has successfully synchronized its clock, typically with VeloCloud Gateways or configured NTP servers.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --clock_sync
{
  "Error": "No gateways found!"
}
```
In the example above, the Edge is reporting an error state where it cannot find any Gateways to synchronize its clock with. A successful synchronization would typically show details about the synchronized time and the source.

##  Field descriptions
| Field | Description |
|---|---|
| Error |  Indicates an error condition encountered during the clock synchronization process. In the example, "No gateways found!" means the Edge could not identify any VeloCloud Gateways to synchronize its time with. Other messages might indicate different issues like NTP server unreachability. If clock synchronization is successful, this field might be absent or show a success status. |