#	--pnat_1to1 [[all | segment-id] [all | v4 | v6]]

##	Description
Displays the 1:1 Network Address Translation (NAT) rules that are part of configured business policies on the VeloCloud Edge. These rules allow for a direct, static mapping of an internal (private) IP address to an external (public) IP address, often used for services hosted behind the Edge that need to be accessible from external networks. The rules are derived from business policies configured in the VeloCloud Orchestrator.

##	Arguments (optional)
The command accepts up to two optional positional arguments.
Usage: `debug --pnat_1to1 [all | segment-id] [all | v4 | v6]`

| Argument     | Description                                                                                                                                                              |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `all`        | As the first argument, displays rules for all segments. This is the default if the first argument is omitted. As the second argument, displays rules for both IPv4 and IPv6. This is the default if the second argument is omitted. If no arguments are provided, the command defaults to `all all`. |
| `segment-id` | (First argument) An integer identifying the VeloCloud segment. If specified, only 1:1 NAT rules pertaining to this segment are displayed.                                  |
| `v4`         | (Second argument) Displays only IPv4 1:1 NAT rules. To use this, the first argument (e.g., `all` or a specific `segment-id`) must also be provided.                       |
| `v6`         | (Second argument) Displays only IPv6 1:1 NAT rules. To use this, the first argument (e.g., `all` or a specific `segment-id`) must also be provided.                       |

##	Example usage
```
example_com:velocli> debug --pnat_1to1
```
This example executes the command with default arguments, displaying all 1:1 NAT rules for all segments and for both IPv4 and IPv6 address families.

##	Field descriptions
The command outputs a list of the active 1:1 NAT rules. The specific columns and exact output format may vary, but typically include information such as:

| Column                | Description                                                                      |
|-----------------------|----------------------------------------------------------------------------------|
| Segment ID            | The identifier of the network segment to which the NAT rule applies.             |
| Business Policy Name  | The name of the business policy that defines this 1:1 NAT rule.                  |
| Inside IP Address     | The internal (LAN-side) IP address that is being translated.                     |
| Outside IP Address    | The external (WAN-side) IP address to which the internal IP address is mapped.   |
| WAN Interface         | The specific WAN link or interface on the Edge used for this NAT mapping.        |
| State / Status        | Indicates the operational status of the NAT rule (e.g., active, inactive).       |
| IP Version            | Indicates whether the rule applies to IPv4 or IPv6 addresses.                    |