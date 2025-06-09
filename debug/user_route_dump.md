#	--user_route_dump [all|segment] [all|v4|v6] [all|prefix] [all|preferred]

##	Description
Displays user-configured routes, primarily intended for remote diagnostic purposes. This command allows for filtering the route dump based on segment, IP version (IPv4 or IPv6), specific network prefixes, and route preference. When filtering by preference, selecting `preferred` will show only the best reachable route, or the first unreachable route if none are reachable. Selecting `all` for preference will display all routes matching the other filters. This command is often used in remote diagnostic procedures to inspect the routing table.

##  Arguments (optional)
These arguments are positional. If an argument is not specified, it defaults to `all`.

| Argument Description | Position | Values | Default | Details |
|---|---|---|---|---|
| Segment filter | 1st | `all` \| `segment-id` | `all` | Specifies the segment for which to display routes. Use `all` for all segments or provide a specific segment ID. |
| IP version filter | 2nd | `all` \| `v4` \| `v6` | `all` | Filters routes by IP version. `all` for both IPv4 and IPv6, `v4` for IPv4 only, `v6` for IPv6 only. |
| Prefix filter | 3rd | `all` \| `prefix` | `all` | Filters routes by a specific network prefix (e.g., `192.168.1.0/24`). Use `all` to display routes for all prefixes. |
| Preference filter | 4th | `all` \| `preferred` | `all` | Determines which routes to display based on their preference and reachability: <br> - `all`: Dumps all routes matching the other filters. <br> - `preferred`: Dumps only the best reachable route. If no reachable routes exist for a given prefix, the first unreachable route is dumped. |

##  Example usage
The following example shows how to invoke the command without any specific filters, which will default to displaying all routes for all segments, IP versions, and prefixes.
```
example_com:velocli> debug --user_route_dump
{
  "segment": [
    {
      "id": 0,
      "name": "Global Segment",
      "routes": [
        // Route objects for the Global Segment would be listed here.
        // The example output is truncated for brevity.
      ]
    },
    {
      "id": 1,
      "name": "Corporate Segment 1",
      "routes": [
        // Route objects for Corporate Segment 1 would be listed here.
      ]
    }
    // Potentially more segments and their routes
  ]
}
```

##  Field descriptions
The output is in JSON format, structured as follows:

| Field     | Parent          | Type    | Description                                                                                                                                                                                             |
|-----------|-----------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `segment` | Root object     | Array   | An array of segment objects, where each object represents a configured network segment on the VeloCloud Edge.                                                                                             |
| `id`      | `segment` object | Number  | The numerical identifier of the segment. For example, `0` typically represents the "Global Segment".                                                                                                      |
| `name`    | `segment` object | String  | The descriptive name of the segment (e.g., "Global Segment", "Corporate Segment").                                                                                                                      |
| `routes`  | `segment` object | Array   | An array of route objects specific to this segment. Each route object contains detailed information about a user-configured route, such as its destination prefix, next hop, metrics, type, and flags. The specific fields within each route object are comprehensive and similar in nature to those provided by other routing table dump commands. |