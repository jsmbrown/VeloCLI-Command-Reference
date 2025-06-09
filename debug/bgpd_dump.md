#	--bgpd_dump

##	Description
This command displays the status of the Border Gateway Protocol (BGP) database on the VeloCloud Edge. It provides insights into the BGP daemon's current state, including information about BGP peers, learned routes, and other operational parameters. This is useful for troubleshooting BGP routing issues within the SD-WAN environment.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --bgpd_dump
```
*(The output of this command will be a dump of BGP daemon status information, which can be extensive and vary based on the BGP configuration and current state. It is not typically presented in a fixed tabular format.)*

##  Field descriptions
The output of `debug --bgpd_dump` is a direct dump of the BGP daemon's internal status and database. It does not have a fixed columnar output. The information displayed will include details such as:
*   BGP router ID
*   Configured BGP neighbors (peers) and their status (e.g., Idle, Connect, Active, OpenSent, OpenConfirm, Established)
*   AS numbers
*   Uptime of BGP sessions
*   Number of prefixes received, advertised, and accepted
*   BGP routing table information
*   Error messages or status codes related to BGP operations

Interpreting the output requires familiarity with BGP concepts and terminology.