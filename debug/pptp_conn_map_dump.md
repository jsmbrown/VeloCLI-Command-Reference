# --pptp_conn_map_dump

## Description
Dumps the table that maps PPTP control channel connection information to corresponding GRE callid values. This information is utilized by the VeloCloud Edge to manage Point-to-Point Tunneling Protocol (PPTP) sessions by associating TCP control connections with their respective Generic Routing Encapsulation (GRE) data tunnels.

## Arguments
This command does not take any arguments.

## Example usage
```
example_com:velocli> debug --pptp_conn_map_dump
[]
```

## Field descriptions
| Output | Description |
|---|---|
| `[]` | An empty array. This output indicates that the PPTP connection map on the VeloCloud Edge is currently empty. There are no active PPTP control channel connections mapped to GRE call IDs at the time the command was executed. If such mappings existed, the array would contain entries detailing them, typically including identifiers for the control channel and the associated GRE call ID. |