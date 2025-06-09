# --rsummary [all | &lt;segment-id&gt;]

## Description
Provides a concise summary of the routing table status on the VeloCloud Edge. This includes version numbers for IPv4 and IPv6 route tables and a count of specific route types, such as cloud routes. The summary can be for all segments or a specific segment.

## Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays the route summary for all configured segments on the Edge. |
| `&lt;segment-id&gt;` | Displays the route summary for the specified segment ID. Replace `&lt;segment-id&gt;` with the numerical ID of the desired segment. |
| *None* | If no arguments are provided, the command typically displays a summary for the default segment or a global summary if the Edge is not segmented. The example below illustrates this usage. |

## Example usage
```json
example_com:velocli> debug --rsummary
[
  {
    "route6_version": 202,
    "route_version": 225,
    "rsummary": {
      "cloud_routes": 3
    }
  }
]
```

## Field descriptions
The output is a JSON array. Each object in the array represents a route summary, potentially one per segment if `all` segments are queried or if the Edge has multiple segments and no specific segment ID is provided. The fields within each JSON object are described below:

| Field             | Description |
|-------------------|-------------|
| `route6_version`  | Integer. The current version number of the IPv6 routing table on the VeloCloud Edge. This version increments each time the IPv6 routes are updated. |
| `route_version`   | Integer. The current version number of the IPv4 routing table on the VeloCloud Edge. This version increments each time the IPv4 routes are updated. |
| `rsummary`        | JSON Object. Contains key-value pairs summarizing different categories of routes. |
| `rsummary.cloud_routes` | Integer. The number of "cloud routes." These are routes learned dynamically through the VeloCloud SD-WAN overlay network. This includes routes to other VeloCloud Edges (e.g., via Dynamic Edge to Edge - DE2E), Hub Edges, or VeloCloud Gateways, managed by protocols like VeloCloud Routing Protocol (VCRP). |