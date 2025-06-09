#	--transient_td_dump

##	Description
This command displays information about transient Tunnel Descriptors (TDs) on the VeloCloud Edge. Transient TDs represent temporary or dynamically established paths, such as those created for Dynamic Edge to Edge (DE2E) tunnels. If transient paths exist, their details are listed. If no transient paths are found, a corresponding message is displayed, as shown in the example.

##	Arguments
None.

##	Example usage
```
example_com:velocli> debug --transient_td_dump
No transient paths found
```

##	Field descriptions
The example output indicates that no transient paths were found at the time the command was run. If transient paths (e.g., dynamic tunnels established via DE2E) were active, the output would list them. The specific columns and their meanings would be detailed here, likely including information such as:
*   Path or Tunnel Identifiers
*   Peer Edge information (e.g., Name, ID)
*   Tunnel status (e.g., Up, Down)
*   Interface or Link information used for the transient path
*   Timestamps related to path establishment or lifetime