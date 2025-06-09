#	--bgp_sync_list

##	Description
Dumps the BGP (Border Gateway Protocol) Sync view entries on a VeloCloud Edge. BGP is a standardized exterior gateway protocol used to exchange routing and reachability information between autonomous systems. Within the VeloCloud SD-WAN solution, BGP is commonly used for route exchange between Edges and customer LAN-side routers, or between Edges/Gateways and Non-VeloCloud Sites (NVS/NSD). The "Sync view entries" likely refer to the internal state or list of BGP routes that are being processed, synchronized, or considered for advertisement by the Edge's BGP process, reflecting how these routes interact with the VeloCloud overlay routing (VCRP). This command is useful for troubleshooting BGP route propagation and synchronization issues.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --bgp_sync_list
```
*(Note: The output format for this command is not provided in the example. The command will display a list or table of BGP synchronization entries.)*

##  Field descriptions
| Column | Description |
|---|---|
|   |  *(Specific output fields depend on the command's output, which is not available in the provided example. Generally, this would include details about BGP prefixes, peer information, synchronization status, and attributes.)* |