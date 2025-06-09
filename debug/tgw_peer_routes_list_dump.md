# --tgw_peer_routes_list_dump [[all | prefix] [all | segment-id]]

## Description
This command dumps the list of TGW (Transit Gateway) Peer Routes known by the VeloCloud Edge. TGW peer routes are typically those learned from or advertised to a network transit hub, often in a cloud environment, with which the Edge is peering.

## Arguments (optional)
The command accepts up to two optional positional arguments. If no arguments are provided, it defaults to showing all routes for all segments.

| Argument     | Description                                                                                                                               |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all`        | When used as the first argument, displays routes for all prefixes. When used as the second argument, displays routes for all segment IDs. If no arguments are provided, `all` is assumed for both. |
| `prefix`     | As the first argument, specifies a network prefix (e.g., `192.168.1.0/24` or `2001:db8::/32`) to filter the TGW peer routes.                 |
| `segment-id` | As the second argument, specifies a segment ID (e.g., `1`, `100`) to filter the TGW peer routes.                                            |

## Example usage
To display all TGW peer routes for all segments:
```
example_com:velocli> debug --tgw_peer_routes_list_dump
```

To display TGW peer routes for a specific prefix (e.g., 10.0.0.0/8) across all segments:
```
example_com:velocli> debug --tgw_peer_routes_list_dump 10.0.0.0/8
```

To display TGW peer routes for all prefixes within a specific segment (e.g., segment 1):
```
example_com:velocli> debug --tgw_peer_routes_list_dump all 1
```

To display TGW peer routes for a specific prefix (e.g., 10.0.0.0/8) within a specific segment (e.g., segment 1):
```
example_com:velocli> debug --tgw_peer_routes_list_dump 10.0.0.0/8 1
```
*(Note: The specific output format for this command was not provided in the input. The output would typically be a list of routes with details such as destination, next hop, metric, etc.)*

## Field descriptions
| Column | Description |
|---|---|
|   | (Specific output fields for this command are not detailed as no sample output was provided.) |